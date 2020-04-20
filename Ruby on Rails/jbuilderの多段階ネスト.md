```rb
json.array! @railway_company do |railway_company|
  json.code railway_company.code
  json.name railway_company.name

  json.railway_lines railway_company.railway_lines do |railway_line|
    json.code railway_line.code
    json.name railway_line.name

    json.stations railway_line.stations do |station|
      json.code station.code
      json.name station.name
    end
  end
end
```
