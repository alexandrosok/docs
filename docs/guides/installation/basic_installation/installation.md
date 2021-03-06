![SeAT](https://i.imgur.com/aPPOxSK.png)

# Basic Installation

This guide aims to provide most users a simple step-by-step guide to having a running SeAT instance. SeAT provides two simple installation scripts. You would need to choose if you would rather use Docker (which is recommended) or the SeAT tool.

!!! note

    Make sure you review the [hardware](/general/requirements/) requirements before installing anything intended for production use!

<section class="mdc-tabs">
<ul class="mdc-tab-bar">
  <li class="mdc-tab active"><a role="tab" data-toggle="tab">Docker</a></li>
  <li class="mdc-tab"><a role="tab" data-toggle="tab">SeAT Tool</a></li>
</ul>
<div class="mdc-panels">
<div role="tabpanel" class="mdc-panel active">

    <p>Getting SeAT installed via Docker is the recommended way of running SeAT. Using docker, all of SeAT's dependencies is neatly abstracted away from your hosts operating system and does not conflict with any pre-existing software you might have on your server. With a little bit of extra work, Docker installations are also possible on Windows.
    <br><br>
    Regardless if you have <code>docker</code> & <code>docker-compose</code> installed on your Linux server, the following script will install them if needed and then download the SeAT <code>docker-compose.yml</code> and <code>.env</code> files to <code>/opt/seat-docker</code> on your server:</p>

    <pre><code class="bash hljs">bash <(curl -fsSL https://git.io/seat-docker)</code></pre>

    <p>Once downloaded, <code>docker-compose up -d</code> is run from that folder to start the SeAT stack. To see this script in action on a fresh Digital Ocean VPS, check out the following asciinema:</p> <script src="https://asciinema.org/a/c0EM0kQnj86JkNX40TBdhA4Ua.js" id="asciicast-c0EM0kQnj86JkNX40TBdhA4Ua" async></script>

    <p>Once the docker installation is complete, you should have SeAT available on the server, listening on port 8080. For more detailed docker related information as well as next steps to configure a web server, please refer to the <a href="/docs/guides/installation/manual_installation/docker">Manual Installation: Docker</a> section.</p>

    <div class="admonition note">
        <p class="admonition-title"> Note</p>
        <p>Please have a look at <a href="/docs/guides/admin/docker">Docker Admin</a> Page for commands for Docker.</p>
    </div>

</div>
<div role="tabpanel" class="mdc-panel">
    <p>A semi automated installation option for Debian 8 / 9, Ubuntu 16.04 / 18.04 LTS and CentOS 6 / 7 is available. To get started with this method, a helper script should be downloaded and run.</p>

    <pre><code class="bash hljs">bash <(curl -fsSL https://git.io/seat-installer)</code></pre>

    <div class="admonition warning">
        <p class="admonition-title"> Warning</p>
        <p> This installer assumes that <i>nothing else</i> is configured on the host operating system. If you have an existing database server or web server on the host this script is run on there is a high chance it will fail!</p>
    </div>

    <p>This will ask you to choose your operating system in order to prepare the <code>seat</code> tool for use.
    <br> Example usage: </p>

    <pre><code class="bash hljs">$ bash <(curl -fsSL https://git.io/seat-installer)
    * SeAT Installer Operating System Selection
    1) CentOS 6    3) Ubuntu 16x  5) Debian 8x   7) Quit
    2) CentOS 7    4) Ubuntu 18x  6) Debian 9x
    * Please select the target operating system:
    </code></pre>

    <p>Once the preparations are done, the installer will prompt you to run <code>seat install:production</code>. </p>

    <div class="admonition note">
        <p class="admonition-title"> Note</p>
        <p>During the beta of SeAT 3x, please run <code>seat install:production --minimum-stability beta</code> instead. This will tell the installer that versions that are marked as non-stable is ok to use.</p>
    </div>

</div>
</section>
