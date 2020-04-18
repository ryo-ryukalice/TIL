```rb
    # 事業会社
    companies = CSV.read('lib/tasks/oneshot/files/company20200309.csv', headers: true)

    # 路線
    lines = CSV.read('lib/tasks/oneshot/files/line20200306free.csv', headers: true)

    # 駅
    stations = CSV.read('lib/tasks/oneshot/files/station20200316free.csv', headers: true)
```
