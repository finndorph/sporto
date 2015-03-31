
```
<?php
session_start();
include_once('lib/sporto.php');
include_once('config/sporto_config.php');
if(!isset($_SESSION['SAML'])) {
    try {
        $sporto = new SPorto($sporto_config);
        $_SESSION['SAML'] = $sporto->authenticate();
    } catch (Exception $e) {
        echo $e->getMessage();
        exit;
    }
}
```
> <h2><a href='#config'>Configuration</a></h2>

> <p>Configuration of SPorto is done by putting the required options<br>
<blockquote>into a simple PHP array.</p>
<p>The following is a list of all options and they are all<br>
required.</p>
<ul>
<blockquote><li>idp_certificate - Certificate from IdP</li>
<li>sso - SingleSignoOnService URL for IdP</li>
<li>private_key - Private key used for signing requests</li>
<li>acs - AssertionConsumerService URL for the SP (SHOULD point to a<br>
script that invokes SPorto)</li>
<li>entityid - entityId for the SP</li>
</blockquote></ul></blockquote>

> <h3><a href='#configexample'>Example configuration</a></h3>

```
$sporto_config = array(
    'idp_certificate' => '...',
    'sso' => '...',
    'private_key' => '...',
    'asc' => '...',
    'entityid' => '...',
);
```
> <h2><a href='#session'>Session management</a></h2>

> <p>SPorto does not contain any session management. It is up to the<br>
<blockquote>containig application to handle this.</blockquote>

