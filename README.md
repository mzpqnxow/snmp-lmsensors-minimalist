# snmp-lmsensors-minimalist

An example of a minimalist read-only SNMPv1 configuration for exposing lmsensors data. This is tested / designed to run on Debian/Ubuntu based systems only. You will obviously need to change the `apt-get` commands to `yum` at the very least to use this on CentOS, RHEL, or Arch.

## Notes

This is for dummies who haven't worked with SNMP much before and don't trust it enough to enable it on their systems. This `Makefile` provides a quick way to install an snmpd configuration that exposes *only* `lmsensors` information by whitelisting the lmSensors OID to a view and assigning a non-default value for the read-only community string name

### Install
 
`$ make install`

### Uninstall
`$ make uninstall`

#### Running as root or using sudo

If you run the `make` commands as root, you will want to comment out the `SUDO := sudo` line in the `Makefile` and uncomment the `SUDO :=` line. This will cause the `Makefile` to skip sudo since most users do not have sudoers rules for the root user and sudo will not, by default, allow root to sudo to other users (or itself)


### If I don't run Debian or Ubuntu because I think I am so cool for using Arch ...

1. Use the Arch package manager (whose name I am too lazy to even look up right now) to install snmpd
2. Copy etc/snmp/snmpd.conf over /etc/snmpd.conf
3. Edit /etc/snmpd.conf by hand to change ____COMMSTR____ to your preferred community string value
4. Regret wasting your time on Arch when Debian works just fine :>
