# Nginx AWS Sync

AWS instances to upstream servers

## Requirements

* `python3`
* `pip3`

## Dependencies

`pip3 install -r requirements.txt`

## Example

**Nginx upstram configuration:**

```sh
upstream backend {
    include /var/lib/nginx/upstream/backend.conf;
}
```

**Upstream File:** `/var/lib/nginx/upstream/backend.conf`

```sh
server 0.0.0.1 down;
```

**AWS:**
_Instance tags..._

| Name | `Upstream` | ... |
|---|---|---|
| my_server-1 | `backend` | ... |
| my_server-2 | `backend` | ... |
| my_server-3 | `foo` | ... |

**Create a `root` cron:**

```sh
# Nginx AWS Sync - AWS instances to upstream servers
* * * * * root /path/to/nginx-aws-sync -c /path/to/config.yaml >> /var/log/nginx-aws-sync.log 2>&1
```
