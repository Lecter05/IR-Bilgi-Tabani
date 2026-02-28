4624
**Logon Type ile daralt**
Workstation Name ile ip adresi aynı aygıta ait değilse saldırı demek.

`4776` (NTLM authentication) / `4625` (failed logon) / `4688` (process creation — eğer responder/relay araçları çalıştırıldıysa) / `4768` (Kerberos anomalies) ile ilişkilendir.

4688
`python responder.py`, `ntlmrelayx.py`, `impacket`