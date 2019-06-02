# IM7 layer for AWS Lambda

Based on instructions at https://gist.github.com/bensie/56f51bc33d4a55e2fc9a and https://github.com/tempusenergy/glpk-lambda-layer

## Usage

Clone the repo and run the profile.sh bash script. This will install the layer.zip as a layer.

You can then attach that layer to your lambda functions and IM7 binaries will be available in `/opt/bin/` on those layers.

### Overriding the existing IM6

You'll need to patch your path to ensure the IM7 binaries (and the libraries) are available as preference to the IM6 which comes pre-installed

##### Ruby
``` ruby
ENV['PATH'] = '/opt/bin:' + ENV['PATH']
ENV['LD_LIBRARY_PATH'] = '/opt/lib:' + ENV['LD_LIBRARY_PATH']
```

##### Others
... please raise a PR with other languages. It's essentially adding to the env variables `PATH` and `LD_LIBRARY_PATH`

