---


---

<h1 id="docker-cp"><a href="https://docs.docker.com/engine/reference/commandline/container_cp/">docker cp</a></h1>
<p>Equivalent to  <code>docker container cp</code></p>
<p>The <code>docker cp</code> utility copies the contents of <code>SRC_PATH</code> to the <code>DEST_PATH</code>. You can copy from the container’s file system to the local machine or the reverse.</p>
<p><strong>exemples :</strong></p>
<p>Copy a local file into container :</p>
<pre class=" language-console"><code class="prism  language-console"> docker cp SRC_PATH CONTAINER:DEST_PATH
</code></pre>
<p>Copy files from container to local path :</p>
<pre class=" language-console"><code class="prism  language-console">docker cp CONTAINER:DEST_PATH SRC_PATH
</code></pre>
<blockquote>
<p>Written with <a href="https://stackedit.io/">StackEdit</a>.</p>
</blockquote>

