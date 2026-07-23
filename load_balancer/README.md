# Load Balancer

This project covers setting up multiple web servers behind a load balancer,
building on the Nginx configuration skills from the `web_server` project.

## Background

Running a single web server creates a single point of failure and limits
how much traffic you can handle. Placing multiple servers behind a load
balancer solves this — traffic gets distributed across servers, improving
both availability and performance. This project starts by preparing a
second web server (`web-02`) identical to `web-01`, and adds a way to
identify which server is responding to a given request.

## Tasks

### 0. Double the number of webservers

Configures `web-02` to be identical to `web-01` by installing and
configuring Nginx. To make it possible to track which server answers a
given request (useful for verifying load balancer behavior later), Nginx
is configured to add a custom `X-Served-By` response header set to the
server's hostname.

**File:** [`0-custom_http_response_header`](./0-custom_http_response_header)

**Requirements:**
- Nginx installed and running on both `web-01` and `web-02`
- HTTP responses include a custom header: `X-Served-By: <hostname>`
- Script configures a brand new Ubuntu machine from scratch

**Usage:**
```bash
./0-transfer_file 0-custom_http_response_header <SERVER_IP> ubuntu <PATH_TO_SSH_KEY>
ssh -i <PATH_TO_SSH_KEY> ubuntu@<SERVER_IP>
sudo ./0-custom_http_response_header
```

**Verification:**
```bash
curl -sI <SERVER_IP> | grep X-Served-By
```

## Author

Orion Seruvumba
