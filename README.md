# RSpec::Retry


RSpec::Retry adds a ``:retry`` option for intermittently failing rspec examples.
If an example has the ``:retry`` option, rspec will retry the example the
specified number of times until the example succeeds. Read more about
RSpec::Retry's base functionality at [here](https://github.com/NoRedInk/rspec-retry).

## Retry until fail

We use this fork to aid in resolving finicky specs by running the spec many
times over, until it fails (in which case we know that the spec is still
finicky) or it passes a convincing number of times in a row.

To use it, you must first add it to your Gemfile:

`gem 'rspec-retry', :git => 'git://github.com/grnhse/rspec-retry.git'`

**Please be sure to revert this change to the Gemfile before merging your branch.**

Mark the test(s) you want to run and the maximum number of retries by adding
the following metadata to the it block:
`:retry_until_fail => true, :retry => (Integer)`

E.g.

```
describe “A finicky spec” do
  it ‘will fail?’, :retry_until_fail => true, :retry => 20 do
    …
  end
end
```
