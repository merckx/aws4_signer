# Aws4Signer - Simple signer module implements AWS4 signature

## Installation

Add this line to your application's Gemfile:

    gem 'aws4_signer'

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install aws4_signer

## Usage

```
bucket, key = 'foo', 'path/to/file'
signer = AWS4Signer.new(ENV["AWS_ACCESS_KEY_ID"], ENV["AWS_SECRET_ACCESS_KEY"], 'ap-northeast-1', 's3')
uri = URI("https://s3-ap-northeast-1.amazonaws.com/#{bucket}/#{key}")
Net::HTTP.start(uri.host, uri.port, use_ssl: true) do |http| 
  req = Net::HTTP::Get.new(uri)
  signer.sign_http_request(req)

  response = http.request(req)
  p response.body
end
```


## Contributing

1. Fork it ( https://github.com/sorah/aws4_signer/fork )
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create a new Pull Request