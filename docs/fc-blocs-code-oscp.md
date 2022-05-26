# Les blocs de Code HTML "OSCP"

## Mise en évidence

Trois types de mise en évidence "OSCP" (̀`2012-code-block`) sont disponbibles en utilisant des balises spécifiques, les noms des balises correspondent à l'utilisation qui semblent en être faite dans le document de référence :

```html
<pre><code>
kali@kali:~$ <oscp-cmd>searchsploit afd windows</oscp-cmd>
<oscp-parameter>local</oscp-parameter>
...
<oscp-hacked>Microsoft Windows XP/2003 | windows/local/6757.txt</oscp-hacked>
...
<!-- les anciennes balise mark + class oscp sont toujours disponibles-->
</code></pre>
```
<figcaption>Exemple de mise en évidence d'une partie du listing</figcaption>

<pre><code>
kali@kali:~$ <oscp-cmd>searchsploit afd windows</oscp-cmd> <oscp-parameter>local</oscp-parameter>
---------------------------------------------------------------- ---------------------------------
 Exploit Title                                                  |  Path
---------------------------------------------------------------- ---------------------------------
Microsoft Windows (x86) - 'afd.sys' Local Privilege Escalation  | windows_x86/local/40564.c
<oscp-hacked>Microsoft Windows 7 (x86) - 'afd.sys' Dangling Pointer Privileg | windows_x86/local/39446.py</oscp-hacked>
Microsoft Windows XP - 'afd.sys' Local Kernel Denial of Service | windows/dos/17133.c
<mark class="oscp-hacked">Microsoft Windows XP/2003 - 'afd.sys' Local Privilege Escalatio | windows/local/6757.txt</mark>
Microsoft Windows XP/2003 - 'afd.sys' Local Privilege Escalatio | windows/local/18176.py
---------------------------------------------------------------- ---------------------------------
Shellcodes: No Result
kali@kali:~$
</code></pre>
<figcaption>Résultat "OSCP"</figcaption>

## Passage à la ligne

Le passage à la ligne n'est pas activé par défaut, car ce type de bloc de code est principalement utilisé pour illustrer le résultat de commande ; le passage à la ligne peut ne pas être le résultat attendu mais il est possible de l'activer à l'aide de la classe `fc-pdf-white-space-pre-wrap` :

```html
<pre class="fc-pdf-white-space-pre-wrap"><code>
Most field in overwritten (corrupted) srvnet struct can be any value ...
```
<figcaption>Exemple de bloc de code avec passage à la ligne forcée</figcaption>


<pre class="fc-pdf-white-space-pre-wrap"><code>
Most field in overwritten (corrupted) srvnet struct can be any value because it will be left without free (memory leak) after processing
Here is the important fields on x64
- offset 0x58 (VOID*) : pointer to a struct contained pointer to function. the pointer to function is called when done receiving SMB request.
                          The value MUST point to valid (might be fake) struct.
- offset 0x70 (MDL)   : MDL for describe receiving SMB request buffer
  - 0x70 (VOID*)    : MDL.Next should be NULL
  - 0x78 (USHORT)   : MDL.Size should be some value that not too small
  - 0x7a (USHORT)   : MDL.MdlFlags should be 0x1004 (MDL_NETWORK_HEADER|MDL_SOURCE_IS_NONPAGED_POOL)
  - 0x80 (VOID*)    : MDL.Process should be NULL
  - 0x88 (VOID*)    : MDL.MappedSystemVa MUST be a received network buffer address. Controlling this value get arbitrary write.
                        The address for arbitrary write MUST be subtracted by a number of sent bytes (0x80 in this exploit).
</code></pre>
<figcaption>Résultat du passage à la ligne forcée</figcaption>


