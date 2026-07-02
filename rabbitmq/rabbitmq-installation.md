# 4. RabbitMQ Installation

This section covers installation of Erlang and RabbitMQ on all 3 nodes.

## 4.1 Install Required Packages

Run on all nodes:

```bash
sudo dnf update -y
sudo dnf install -y curl wget socat logrotate
4.2 Install Erlang
sudo dnf install -y erlang

Verify:

erl -version
4.3 Add RabbitMQ Repository
sudo tee /etc/yum.repos.d/rabbitmq.repo <<EOF
[rabbitmq]
name=rabbitmq
baseurl=https://packagecloud.io/rabbitmq/rabbitmq-server/el/9/\$basearch
gpgcheck=1
repo_gpgcheck=1
enabled=1
gpgkey=https://packagecloud.io/rabbitmq/rabbitmq-server/gpgkey
EOF
4.4 Install RabbitMQ Server
sudo dnf install -y rabbitmq-server
4.5 Enable and Start Service
sudo systemctl enable rabbitmq-server
sudo systemctl start rabbitmq-server

Check status:

sudo systemctl status rabbitmq-server
4.6 Enable Management Plugin
sudo rabbitmq-plugins enable rabbitmq_management

Restart service:

sudo systemctl restart rabbitmq-server
4.7 Verify Installation
sudo rabbitmqctl status
4.8 Access Management UI

Open in browser:

http://<node-ip>:15672

Default credentials:

username: guest
password: guest
