`require 'rspec/expectations'` して `include RSpec::Matchers` すればカジュアルにテストできる。

```rb
require 'rspec/expectations'

include RSpec::Matchers

task use_expect: :environment do
  expect(1).to eq 1
end
```
