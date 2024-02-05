---


---

<h1 id="docker-exec"><a href="https://docs.docker.com/engine/reference/commandline/container_exec/#:~:text=Description,working%20directory%20of%20the%20container.">docker exec</a></h1>
<p>Equivalent to  <code>docker container exec</code></p>
<p>The <code>docker exec</code> command runs a new command in a running container.</p>
<p><strong>exemples :</strong></p>
<p>Open a terminal in <code>CONTAINER</code> :</p>
<pre class=" language-console"><code class="prism  language-console">docker exec -it CONTAINER bash
</code></pre>
<p><strong>usefull options :</strong></p>

<table>
<thead>
<tr>
<th>option</th>
<th>description</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>-i</code> or <code>--interactive</code></td>
<td>Keep STDIN open even if not attached (needed if the command is interactive)</td>
</tr>
<tr>
<td><code>-t</code> or <code>--tty</code></td>
<td>Allocate a pseudo-TTY (needed with <code>-i</code> to open a terminal in a container)</td>
</tr>
</tbody>
</table><blockquote>
<p>Written with <a href="https://stackedit.io/">StackEdit</a>.</p>
</blockquote>

