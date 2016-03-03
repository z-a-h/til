#Hash Fetch

When you expect a Hash to contain a key, use `fetch()` rather than `[]`.
If the key doesn't exists, `fetch()` will raise an exception where as `[]` will return a `nil` value.

[source](http://brewhouse.io/2016/02/26/five-practices-for-robust-ruby-on-rails-applications.html?utm_source=rubyweekly&utm_medium=email)