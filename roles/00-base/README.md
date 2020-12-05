# Base System Build 
This ansible role is considered to be the base hardened build for all *nix based systems within the environment.

## Supported OS
The following Operating Systems Are Currently Supported:
+ Ubuntu
    + 18.04 LTS (Bionic)
    + 20.04 LTS (Focal)


## Overview
The tasks are split into multiple sections in order to improve maintainability, the goal for this base install is to provide a minimum set of hardening to a system in order to ensure a minimum level of security is applied. 

## Hardening Performed

### Harden System
 + Safe Package Upgrade
 + Restrict Core Dumps
 + Enable ASLR
 + Remove Profile & RC UMASK
 + Set Default UMASK To 077

 ### Configure UFW
 + Permit SSH (22/tcp)
 + Set Default INCOMING Policy To Block

 ### Harden Root Account
 +  Restrict root Login - access.conf
 +  Restrict root Login - securetty

 ### Harden SSH
  + Disallow root Access
  + Ensure Permissions on '/etc/ssh/sshd_config'
  + Ensure SSH Protocol = 2
  + Set MaxAuthTries = 4
  + Enable IgnoreRhosts
  + Ensure Idle Timeout
    + ClientAliveInterval = 300
    + ClientAliveCountMax = 0
  + Set LoginGraceTime = 60
  + Ensure Strong MAC Algos
    + hmac-sha2-512-etm@openssh.com
    + hmac-sha2-256-etm@openssh.com
    + umac-128-etm@openssh.com
    + hmac-sha2-512
    + hmac-sha2-256
    + umac-128@openssh.com
 + Ensure Strong Ciphers
    + aes256-gcm@openssh.com
    + chacha20-poly1305@openssh.com
    + aes128-gcm@openssh.com
    + aes256-ctr
    + aes192-ctr
    + aes128-ctr
+ Ensure Strong Key Exchange Ciphers
    + curve25519-sha256@libssh.org
    + diffie-hellman-group-exchange-sha256