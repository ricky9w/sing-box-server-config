# 使用 Cloudflare WARP 作为出站

### 注册 warp 账号

使用 [warp-reg.sh](https://github.com/chise0713/warp-reg.sh), 注册warp账号:

```sh
bash -c "$(curl -L warp-reg.vercel.app)"
```

参考: [sing-box-examples/wireguard.md at main · chika0801/sing-box-examples](https://github.com/chika0801/sing-box-examples/blob/main/wireguard.md)

示例输出:

```json
{
  "endpoint":{
    "v4": "<ipv4-endpoint>",
    "v6": "<ipv6-endpoint>",
  },
  "reserved_dec": [170, 170, 170],
  "reserved_hex": "0xaaaaaa",
  "reserved_str": "qqqq",
  "private_key": "<private-key>",
  "public_key": "bmXOC+F1FxEMF9dyiK2H5/1SUtzH0JuVo51h2wPfgyo=",
  "v4": "172.16.0.2",
  "v6": "<ipv6-local-address>"
}
```

outbound 示例:

```json
{
  "tag": "warp",
  "type": "wireguard",
  "server": "<endpoint>", // IPv4/IPv6 endpoint, 或域名 engage.cloudflareclient.com
  "server_port": 2408,
  "local_address": [
    "172.16.0.2/32", 
    "<ipv6-local-address>" // 填写上面的 "v6" 地址
  ],
  "private_key": "private-key",
  "peer_public_key": "bmXOC+F1FxEMF9dyiK2H5/1SUtzH0JuVo51h2wPfgyo=",
  "reserved": [170, 170, 170], // 填写上面的 "reserved_dec"
  "mtu": 1280
}
```
