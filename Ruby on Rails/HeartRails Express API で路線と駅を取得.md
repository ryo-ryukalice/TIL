```rb
    # エリア
    res = Net::HTTP.get(URI('http://express.heartrails.com/api/json?method=getAreas'))
    areas = JSON.parse(res)['response']['area']

    # 路線
    lines = areas.flat_map do |area|
      res = Net::HTTP.get(URI("http://express.heartrails.com/api/json?method=getLines&#{{ area: area }.to_query}"))
      JSON.parse(res)['response']['line']
    end.uniq

    # 駅
    stations = lines.flat_map do |line|
      res = Net::HTTP.get(URI("http://express.heartrails.com/api/json?method=getStations&#{{ line: line }.to_query}"))
      JSON.parse(res)['response']['station'].map { |s| s.slice('name', 'prefecture', 'line', 'x', 'y') }
    end
```

```zsh
> lines
=> ["JR函館支線",
 "JR函館本線",

> stations
=> [{"name"=>"大沼", "prefecture"=>"北海道", "line"=>"JR函館支線", "x"=>140.669347, "y"=>41.971954},
 {"name"=>"池田園", "prefecture"=>"北海道", "line"=>"JR函館支線", "x"=>140.700333, "y"=>41.990692},
```
