## Java SDK 1.7 설치
```
sudo yum list java*jdk-deve
sudo yum install -y java-1.7.0-openjdk-devel.x86_64
sudo rpm -qa java*jdk-devel
javac -version
```

## ngringer controller
### ngrinder controller 설치
```
sudo curl -L -o ngrinder-controller.war https://github.com/naver/ngrinder/releases/download/ngrinder-3.4.1-20170131/ngrinder-controller-3.4.1.war
sudo java -XX:MaxPermSize=200m -jar ngrinder-controller.war --port 8080
 
sudo firewall-cmd --permanent --zone=public --add-port=8080/tcp
sudo firewall-cmd --permanent --zone=public --add-port=16001/tcp
sudo firewall-cmd --permanent --zone=public --add-port=12000-12010/tcp
sudo firewall-cmd --reload
```
### ngrinder controller 실행
```
sudo java -XX:MaxPermSize=200m -jar /root/ngrinder/ngrinder-controller.war ngrinder-controller.war --port 8080
```

## ngrinder agent
### ngrinder agent 설치
```
sudo wget -O ngrinder-agent.tar http://192.168.0.60:8080/agent/download
sudo tar xvf ngrinder-agent.tar
cd ngrinder-agent
```

### ngrinder agent 실행
#### 포트 open
```
sudo firewall-cmd --permanent --zone=public --add-port=0-65535/tcp
sudo firewall-cmd --reload
```

#### foreground 실행
```
sudo run_agent.sh
```

#### background 실행
```
sudo run_agent_bg.sh
```


## ngrinder monitor
### ngrinder monitor 설치
```
sudo wget -O ngrinder-monitor.tar http://192.168.0.60:8080/monitor/download
sudo tar xvf ngrinder-monitor.tar
cd ngrinder-monitor
```

### ngrinder monitor 실행
#### 포트 open
```
sudo firewall-cmd --permanent --zone=public --add-port=13243/tcp
sudo firewall-cmd --reload
```

#### foreground 실행
```
sudo run_monitor.sh
```

#### background 실행
```
sudo run_monitor_bg.sh
```
