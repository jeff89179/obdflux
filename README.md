你好！
很冒昧用这样的方式来和你沟通，如有打扰请忽略我的提交哈。我是光年实验室（gnlab.com）的HR，在招Golang开发工程师，我们是一个技术型团队，技术氛围非常好。全职和兼职都可以，不过最好是全职，工作地点杭州。
我们公司是做流量增长的，Golang负责开发SAAS平台的应用，我们做的很多应用是全新的，工作非常有挑战也很有意思，是国内很多大厂的顾问。
如果有兴趣的话加我微信：13515810775  ，也可以访问 https://gnlab.com/，联系客服转发给HR。
# obdflux

> An agent for collecting automotive metrics from [OBD-II](https://en.wikipedia.org/wiki/On-board_diagnostics) system on InfluxDB

*Currently, this project is a **WORK IN PROGRESS**, so consider it useful for experimentation. Use at your own risk.*

## Building

```
GO111MODULE=on go build
```

## Configuration

`obdflux` requires a running instance of InfluxDB to connect to. You can use your own installation or just use the provided `docker-compose.yml` by:

```
docker-compose up -d
```

Once your InfluxDB is up and running, create a new database by running:

```
docker-compose run influxdb-cli
``` 
then
```
CREATE DATABASE obdflux
```

Finally, create the `.env` file:
```
cp .env.example .env
```

and modify it if needed (or just leave it as is, if you're using the included `docker-compose.yml`).


## Usage

To start, you need an `ELM327` compatible device connected to your system and get the path to the device. 
For futher information on how to get the device path, please refer to the Go library [elmobd](https://github.com/rzetterberg/elmobd) which is used by `obdflux` to handle the underlying OBD-II specs and device serial communication.

Once you know the your device path (e.g. `/dev/ttyYOUR_USB_DEVICE`), run `obdflux`:
```
./obdflux --serial=/dev/ttyYOUR_USB_DEVICE
```


## Testing

In order to test `obdflux` without a real device you can use the `--test=true` option. 
Finally, if you need a more verbose output, you can turn on debugging mode by setting `--debug=true` option.

Example:
```
./obdflux --test=true --debug=true
```

## Demo
![Test drive](docs/demo.png)

## License
MIT




