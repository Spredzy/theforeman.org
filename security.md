---
layout: security
title: Security
---

## Security process

We take security issues seriously and welcome responsible disclosure from researchers discovering vulnerabilities in Foreman.  Please email [foreman-security@googlegroups.com](mailto:foreman-security@googlegroups.com) (a private address for the security team) with all reports.

We will endeavour to resolve high severity issues in the current stable release and lower severity issues in the next major release.  Announcements of security issues will be made on [foreman-announce](https://groups.google.com/forum/#!forum/foreman-announce) when a release containing a fix is available to end users and credit will be given to the researcher if desired.

The policy of the project is to treat all newly reported issues as private, and after evaluation, low to medium severity issues will be made public while high severity issues will be fixed under an embargo.  Typically the project supports only one major (x.y) release at a time, though high severity issues may also be fixed in the previous release if it was only recently superseded.

## Security advisories

All security advisories made for Foreman are listed below with their corresponding [CVE identifier](http://cve.mitre.org/).

* [CVE-2014-3691: SSL certificate verification bypass in smart proxy](security.html#2014-3691)
* [CVE-2014-3653: stored cross site scripting (XSS) in template previews](security.html#2014-3653)
* [CVE-2014-3590: user logout vulnerable to CSRF](security.html#2014-3590)
* [CVE-2014-3531: stored cross site scripting (XSS) in operating system names](security.html#2014-3531)
* [CVE-2014-3492: stored cross site scripting (XSS) in YAML preview](security.html#2014-3492)
* [CVE-2014-3491: stored cross site scripting (XSS) in notification dialogs](security.html#2014-3491)
* [CVE-2014-0007: TFTP boot file fetch API permits remote code execution](security.html#2014-0007)
* [CVE-2014-0208: stored cross site scripting (XSS) in search auto-completion](security.html#2014-0208)
* [CVE-2014-0192: provisioning template previews are world-readable](security.html#2014-0192)
* [CVE-2014-0135: Kafo leaves world-readable default_values.yaml file](security.html#2014-0135)
* [CVE-2014-0090: session fixation, new session IDs are not generated on login](security.html#2014-0090)
* [CVE-2014-0089: stored cross site scripting (XSS) on 500 error page](security.html#2014-0089)
* [CVE-2013-4386: SQL injection in host/host group parameter overrides](security.html#2013-4386)
* [CVE-2013-4182: hosts API privilege escalation](security.html#2013-4182)
* [CVE-2013-4180: DoS via hosts controller input conversion](security.html#2013-4180)
* [CVE-2013-2121: bookmarks remote code execution](security.html#2013-2121)
* [CVE-2013-2113: admin user creation, privilege escalation](security.html#2013-2113)
* [CVE-2013-0210: Arbitrary command execution risk in Foreman proxy](security.html#2013-0210)
* [CVE-2013-0187: XMLHttpRequest bypasses authorization](security.html#2013-0187)
* [CVE-2013-0174: exposed hashed root passwords can be retrieved by unauthenticated remote users](security.html#2013-0174)
* [CVE-2013-0173: insecure fixed salt "foreman" for passwords](security.html#2013-0173)
* [CVE-2013-0171: import allows unauthenticated YAML uploads/parsing leading to arbitrary code execution](security.html#2013-0171)
* [CVE-2012-5648: SQL injection through search mechanism](security.html#2012-5648)
* [CVE-2012-5477: world writable files in proxy](security.html#2012-5477)

### Disclosure details

#### <a id="2014-3691"></a>CVE-2014-3691: SSL certificate verification bypass in smart proxy

The smart proxy (foreman-proxy) fails to block connections when no client SSL certificate is supplied, instead permitting any request.  Typically the smart proxy is configured to receive HTTPS requests with a client SSL certificate that is signed by the same CA (certificate authority) as its own, preventing unauthorized access to manage services such as DHCP, DNS and the Puppet CA.

It is strongly recommended to mitigate the problem by restricting access to the smart proxy.  More information on [foreman-announce](https://groups.google.com/forum/#!topic/foreman-announce/jXC5ixybjqo).

Thanks to Michael Moll, Jon McKenzie and Michael Messmore for reporting the issue.

* Affects all known Foreman versions
* Fix released in Foreman 1.6.2 and 1.5.4
* Redmine issue [#7822](http://projects.theforeman.org/issues/7822)
* Red Hat Bugzilla [#1150879](https://bugzilla.redhat.com/show_bug.cgi?id=CVE-2014-3691)

#### <a id="2014-3653"></a>CVE-2014-3653: stored cross site scripting (XSS) in template previews

Provisioning templates can store HTML and then evaluate HTML or JS content when using the editor's preview function.

Thanks to Aaron Stone for reporting this issue.

* Affects all known Foreman versions
* Fix released in Foreman 1.6.1
* Redmine issue [#7483](http://projects.theforeman.org/issues/7483)
* Red Hat Bugzilla [#1145398](https://bugzilla.redhat.com/show_bug.cgi?id=CVE-2014-3653)

#### <a id="2014-3590"></a>CVE-2014-3590: user logout vulnerable to CSRF

The user logout function could be triggered through cross-site request forgery (e.g. a redirect), causing a user to be logged out and lose their active session.

Thanks to Jan Hutař of Red Hat for discovering this issue.

* Affects all known Foreman versions
* Fix released in Foreman 1.6.1
* Redmine issue [#6999](http://projects.theforeman.org/issues/6999)
* Red Hat Bugzilla [#1128108](https://bugzilla.redhat.com/show_bug.cgi?id=CVE-2014-3590)

#### <a id="2014-3531"></a>CVE-2014-3531: stored cross site scripting (XSS) in operating system names

Operating system names and descriptions could store and cause evaluation of HTML in page views, allowing a cross site scripting (XSS) attack against the user.

Thanks to Jan Hutař of Red Hat for discovering this issue.

* Affects all known Foreman versions
* Fix released in Foreman 1.5.2
* Redmine issue [#6580](http://projects.theforeman.org/issues/6580)
* Red Hat Bugzilla [#1108745](https://bugzilla.redhat.com/show_bug.cgi?id=CVE-2014-3531)

#### <a id="2014-3492"></a>CVE-2014-3492: stored cross site scripting (XSS) in YAML preview

The host YAML page, used to preview the Foreman response for the Puppet ENC, will evaluate HTML stored in any host data such as parameters or comments, allowing a cross site scripting (XSS) attack against the user.

* Affects all known Foreman versions
* Fix released in Foreman 1.4.5 and 1.5.1
* Redmine issue [#6149](http://projects.theforeman.org/issues/6149)
* Red Hat Bugzilla [#1108241](https://bugzilla.redhat.com/show_bug.cgi?id=CVE-2014-3492)

#### <a id="2014-3491"></a>CVE-2014-3491: stored cross site scripting (XSS) in notification dialogs

When resources (e.g. a host group) were saved or deleted through the web UI, the name of the resource would be evaluated unsafely inside the notification popup, allowing a cross site scripting (XSS) attack against the user changing the resource.

Thanks to Adam Salah of the Red Hat Satellite 6 QE Team for discovering this issue.

* Affects all known Foreman versions
* Fix released in Foreman 1.4.5 and 1.5.1
* Redmine issue [#5881](http://projects.theforeman.org/issues/5881)
* Red Hat Bugzilla [#1100313](https://bugzilla.redhat.com/show_bug.cgi?id=CVE-2014-3491)

#### <a id="2014-0007"></a>CVE-2014-0007: TFTP boot file fetch API permits remote code execution

The Smart Proxy API for downloading boot files from installation media to the TFTP server was vulnerable to remote code execution exploits.

Thanks to Lukas Zapletal of the Red Hat Foreman Team for discovering this issue.

* Affects all known Foreman versions
* Fix released in Foreman 1.4.5 and 1.5.1
* Redmine issue [#6086](http://projects.theforeman.org/issues/6086)
* Red Hat Bugzilla [#1105369](https://bugzilla.redhat.com/show_bug.cgi?id=CVE-2014-0007)

#### <a id="2014-0208"></a>CVE-2014-0208: stored cross site scripting (XSS) in search auto-completion

The search auto-completion was vulnerable to a stored cross site scripting (XSS) attack via completion of (global/host) parameters in search keys.

Thanks to Jan Hutař of Red Hat for discovering this issue.

* Affects all known Foreman versions
* Fix released in Foreman 1.4.4 and 1.5.0
* Redmine issue [#5471](http://projects.theforeman.org/issues/5471)
* Red Hat Bugzilla [#1094642](https://bugzilla.redhat.com/show_bug.cgi?id=CVE-2014-0208)

#### <a id="2014-0192"></a>CVE-2014-0192: provisioning template previews are world-readable

Provisioning templates previews ("spoof") are accessible without authentication when used with the hostname parameter.

* Affects Foreman 1.4.0 to 1.4.3 inclusive
* Fix released in Foreman 1.4.4 and 1.5.0
* Redmine issue [#5436](http://projects.theforeman.org/issues/5436)
* Red Hat Bugzilla [#1092354](https://bugzilla.redhat.com/show_bug.cgi?id=CVE-2014-0192)

#### <a id="2014-0135"></a>CVE-2014-0135: Kafo leaves world-readable default_values.yaml file

When Kafo (used in the Foreman installer) runs, a /tmp/default_values.yaml file is written to and created with world readable permissions.  This is prone to race-condition attacks and contains default values for all parameters, such as autogenerated passwords.

* Affects all known Kafo versions
* Fix released in Kafo 0.3.17 and 0.5.2 (to Foreman 1.4 and 1.5 repos respectively)
* Redmine issue [#4648](http://projects.theforeman.org/issues/4648)
* Red Hat Bugzilla [#1076335](https://bugzilla.redhat.com/show_bug.cgi?id=CVE-2014-0135)

#### <a id="2014-0090"></a>CVE-2014-0090: session fixation, new session IDs are not generated on login

Upon successful login, a new session ID was not generated for the user, so an attacker who had set the session ID in the request from the user's browser would be able to exploit the escalated session with the user's privileges.

Thanks to Jeremy Choi and Keqin Hong of the Red Hat HSS Pen-Test Team for discovering this issue.

* Affects all known Foreman versions
* Fix released in Foreman 1.4.2
* Redmine issue [#4457](http://projects.theforeman.org/issues/4457)
* Red Hat Bugzilla [#1072151](https://bugzilla.redhat.com/show_bug.cgi?id=CVE-2014-0090)

#### <a id="2014-0089"></a>CVE-2014-0089: stored cross site scripting (XSS) on 500 error page

The 500 error page was vulnerable to stored cross site scripting attacks, where the error message was rendered without HTML encoding.  In addition, bookmarks could be saved by any user with HTML in the name which caused an error when rendering the bookmark list, leading to a 500 error and execution of the HTML in the browser.

Thanks to Jeremy Choi and Keqin Hong of the Red Hat HSS Pen-Test Team for discovering this issue.

* Affects Foreman 1.4.0 to 1.4.1 inclusive
* Fix released in Foreman 1.4.2
* Redmine issue [#4456](http://projects.theforeman.org/issues/4456)
* Red Hat Bugzilla [#1071741](https://bugzilla.redhat.com/show_bug.cgi?id=CVE-2014-0089)

#### <a id="2013-4386"></a>CVE-2013-4386: SQL injection in host/host group parameter overrides

Host and host group parameter overrides (lookup_values) allowed SQL injection from the host FQDN or host group label.

* Fix released in Foreman 1.2.3
* Redmine issue [#3160](http://projects.theforeman.org/issues/3160)
* Red Hat Bugzilla [#1013076](https://bugzilla.redhat.com/show_bug.cgi?id=CVE-2013-4386)

#### <a id="2013-4182"></a>CVE-2013-4182: hosts API privilege escalation

The /api/hosts API was found to provide access to all hosts without checking whether the current user has privileges to view a particular host.

Thanks to Daniel Lobato Garcia of CERN IT-PES-PS for discovering this issue.

* Fix released in Foreman 1.2.2
* Redmine issue [#2863](http://projects.theforeman.org/issues/2863)
* Red Hat Bugzilla [#990374](https://bugzilla.redhat.com/show_bug.cgi?id=CVE-2013-4182)

#### <a id="2013-4180"></a>CVE-2013-4180: DoS via hosts controller input conversion

Power and IPMI boot actions converted user input to symbols, which could lead to memory exhaustion.

Thanks to Marek Hulan of the Red Hat Foreman Team for discovering this issue.

* Fix released in Foreman 1.2.2
* Redmine issue [#2860](http://projects.theforeman.org/issues/2860)
* Red Hat Bugzilla [#989755](https://bugzilla.redhat.com/show_bug.cgi?id=CVE-2013-4180)

#### <a id="2013-2121"></a>CVE-2013-2121: bookmarks remote code execution

Bookmarks could be created in Foreman containing data that was later executed arbitrarily when reading the bookmark.

Thanks to Ramon de C Valle of the Red Hat Product Security Team for discovering this issue.

* Fix released in Foreman 1.2.0
* Redmine issue [#2631](http://projects.theforeman.org/issues/2631)
* Red Hat Bugzilla [#968166](https://bugzilla.redhat.com/show_bug.cgi?id=CVE-2013-2121)

#### <a id="2013-2113"></a>CVE-2013-2113: admin user creation, privilege escalation

Non-admin user with permissions to create or edit other users were able to change the admin flag, or assign roles that they themselves do not have, enabling a privilege escalation.

Thanks to Ramon de C Valle of the Red Hat Product Security Team for discovering this issue.

* Fix released in Foreman 1.2.0
* Redmine issue [#2630](http://projects.theforeman.org/issues/2630)
* Red Hat Bugzilla [#966804](https://bugzilla.redhat.com/show_bug.cgi?id=CVE-2013-2113)

#### <a id="2013-0210"></a>CVE-2013-0210: Arbitrary command execution risk in smart proxy

Requests to the smart proxy Puppet run API were not properly escaped when running the Puppet command, leading to possible arbitrary command execution.

* Fix released in Foreman 1.2.0

#### <a id="2013-0187"></a>CVE-2013-0187: XMLHttpRequest bypasses authorization

XMLHttpRequest or AJAX requests to Foreman were not subject to authorization checks, enabling privilege escalation for authenticated users.

* Fix released in Foreman 1.1

#### <a id="2013-0174"></a>CVE-2013-0174: exposed hashed root passwords can be retrieved by unauthenticated remote users

The external node classifier (ENC) API in Foreman was accessible to any remote host and the output would contain the hashed root psasword (used for unattended installation).  Authentication and authorization features were added to the ENC API to secure this data.

Thanks to Andreas Rogge for discovering this issue.

* Fix released in Foreman 1.1
* Redmine issue [#2069](http://projects.theforeman.org/issues/2069)

#### <a id="2013-0173"></a>CVE-2013-0173: insecure fixed salt "foreman" for passwords

The salt used to hash root passwords (used for unattended installation) was fixed to the string "foreman" instead of being randomized.

* Fix released in Foreman 1.1
* Redmine issue [#2069](http://projects.theforeman.org/issues/2069)

#### <a id="2013-0171"></a>CVE-2013-0171: import allows unauthenticated YAML uploads/parsing leading to arbitrary code execution

Fact and report import APIs in Foreman were accessible to any remote host and accepted YAML input, allowing arbitrary objects to be created on the Foreman server via YAML.  Authentication and authorization features were added to the import APIs to prevent this.

* Fix released in Foreman 1.1
* Redmine issue [#2121](http://projects.theforeman.org/issues/2121)

#### <a id="2012-5648"></a>CVE-2012-5648: SQL injection through search mechanism

Input to the search mechanism in Foreman was not escaped when constructing queries, enabling SQL injection into the resulting query.

* Fix released in Foreman 1.0.2

#### <a id="2012-5477"></a>CVE-2012-5477: world writable files in smart proxy

The smart proxy daemon ran with a umask of 0, causing files and directories written by it to have world-writable bits set.  Files managed by the smart proxy could be modified by local users on the same host.

* Fix released in Foreman 1.1
* Redmine issue [#1929](http://projects.theforeman.org/issues/1929)

## GPG keys

The Foreman project uses multiple GPG keys to sign packages and release artifacts.  All stable releases will be signed by one of the keys.  Nightly and plugin Debian packages will be signed, while nightly and plugin RPM packages will not (this may change in the future).

Signing for the Debian family of operating systems is via secure apt and more information, including verification steps can be found [on the Debian web site](https://wiki.debian.org/SecureApt#Debian_archive_key_expiry).  RPMs themselves are signed and can be verified using `rpm --checksig PACKAGE`.  All yum repository configs set up by foreman-release RPMs or the installer will enable GPG checking by default.

Key management is changing at the time of writing to cycle nightly keys every two years, and issue limited duration keys per stable release.

<div>
  <table class="table table-bordered table-condensed">
    <thead>
      <tr>
        <th>Key ID</th>
        <th>Fingerprint</th>
        <th>Description</th>
        <th>Created</th>
        <th>Expires</th>
        <th>Revoked</th>
        <th>Notes</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td><a href="http://pgp.mit.edu:11371/pks/lookup?op=get&search=0x1DCB15D12CA140EEF4947E5766CF053FE775FF07">E775FF07</a></td>
        <td>1DCB 15D1 2CA1 40EE F494  7E57 66CF 053F E775 FF07</td>
        <td>Foreman Archive Signing Key</td>
        <td style='white-space:nowrap'>2010-11-10</td>
        <td style='white-space:nowrap'></td>
        <td style='white-space:nowrap'><a href="https://groups.google.com/forum/#!topic/foreman-announce/BiIT784Mb7Q">2014-07-08</a></td>
        <td>Used up to Foreman 1.5.1</td>
      </tr>
      <tr>
        <td><a href="http://pgp.mit.edu:11371/pks/lookup?op=get&search=0x7059542D5AEA367F78732D02B3484CB71AA043B8">1AA043B8</a></td>
        <td>7059 542D 5AEA 367F 7873  2D02 B348 4CB7 1AA0 43B8</td>
        <td>Foreman Automatic Signing Key (2014)</td>
        <td style='white-space:nowrap'>2014-07-01</td>
        <td style='white-space:nowrap'>2016-06-30</td>
        <td style='white-space:nowrap'></td>
        <td></td>
      </tr>
      <tr>
        <td><a href="http://pgp.mit.edu:11371/pks/lookup?op=get&search=0xA91E2984667D1F07">667D1F07</a></td>
        <td>503E FA96 89AA AD57 D693  6514 A91E 2984 667D 1F07</td>
        <td>Foreman Release Signing Key (1.6)</td>
        <td style='white-space:nowrap'>2014-08-14</td>
        <td style='white-space:nowrap'>2015-08-14</td>
        <td style='white-space:nowrap'></td>
        <td></td>
      </tr>
    </tbody>
  </table>
</div>

### Key changes in July 2014

In July 2014 after a server was compromised, the existing GPG key (0xE775FF07) was revoked and replaced with a new key (0x1AA043B8) as a precaution.  All existing packages were re-signed with the new key and thereafter, new major releases are signed with new per-release keys.

All users with the old key trusted are urged to immediately disable this as follows:

* Debian users must run `sudo apt-key del E775FF07`
* RPM users must run `sudo rpm -e gpg-pubkey-e775ff07-4cda3cf9`

More information is available in [the announcement](https://groups.google.com/forum/#!topic/foreman-announce/BiIT784Mb7Q).
