# Example logrotate 

```
cd /var/log
cp -a messages output.log
```

```
cd /etc/logrotate.d
vi output_log
```

```
/var/log/output.log {
        size 1k
        create 700 kurs kurs
        rotate 4
}
```

```
systemctl start logrotate.service
ls -la /var/log/output*
```
