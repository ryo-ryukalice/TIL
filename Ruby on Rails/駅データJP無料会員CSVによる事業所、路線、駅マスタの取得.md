```rb
    ApplicationRecord.transaction do
      # 事業会社
      companies = CSV.read('lib/tasks/oneshot/files/company20200309.csv', headers: true)
      companies.each { |c| RailwayCompany.create!(code: c['company_cd'], name: c['company_name']) }

      # 路線
      lines = CSV.read('lib/tasks/oneshot/files/line20200306free.csv', headers: true)
      lines.each { |l| RailwayLine.create!(code: l['line_cd'], company_code: l['company_cd'], name: l['line_name']) }

      # 駅
      stations = CSV.read('lib/tasks/oneshot/files/station20200316free.csv', headers: true)
      stations.each { |s| Station.create!(code: s['station_cd'], line_code: s['line_cd'], name: s['station_name']) }
    end
```
