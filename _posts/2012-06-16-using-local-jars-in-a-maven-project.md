---
layout: post
title: Using local jars in a maven project
redirect_from: /2012/06/using-local-jars-in-a-maven-project
---

<!--:en-->Maven is great, really, but sometimes you just have to use that obscure jar library that isn't in any maven repository. You know, not everyone uses maven.

So, how do you handle this type of dependencies? This is what I do, and you might find it useful: I create a local repository within the project. This way you can put everything in you version control system, and have maven deal with everything. Also, if you have several subprojects using the same library, you can create the local repository in the toplevel.

OK. Sounds good, right? Here's how I do it:
<ol>
	<li>Create a directory under the project. I always use "lib"</li>
	<li>Install the jar libs to this directory using:
{% highlight shell %}
mvn install:install-file -Dfile=<jar_file>  -DgroupId=<groupId> -DartifactId=<artifactId> -Dversion=<version> -Dpackaging=jar -DlocalRepositoryPath=<path_to_lib_dir>
{% endhighlight %}
</li>
	<li>Add the repository to you POM file:
{% highlight xml %}
<repositories>
    <repository>
        <id>lib</id>
        <url>file://${project.basedir}/lib</url>
    </repository>
</repositories>
{% endhighlight %}
</li>
	<li>Add the dependencies for whatever jars you've added to your local repo</li>
	<li>Joy.</li>
</ol>
And that's it. If you want to share a different solution, please do.
<!--:--><!--:pt-->

(PT-BR version below)

---------------

# Usando jars locais num projeto maven

<p>Maven é legal,  mesmo, mas as vezes você tem que usar aquela biblioteca jar obscura que não está em nenhum repositório. Você sabe, né, nem todo mundo usa maven.</p>
<p>Entao, como você lida com essas dependências? Eu faço assim, e talvez alguém acha útil: eu crio um repositório local dentro do projeto. Assim dá pra colocar tudo no git (ou em qualquer outro VCS de sua preferência) e deixar o maven cuidar de tudo. E se você tiver vários subprojetos dependendo ds mesmas bibliotecas, pode criar o repositório dentro do projeto "guarda-chuva".</p>
<p>OK. Parece legal? Como fazer:</p>
<ol>
<li>Crie um diretório dentro do projeto. Eu uso sempre "lib"</li>
<li>Instale os  jars nesse diretório usando o maven:
{% highlight shell %}
mvn install:install-file -Dfile=<jar_file>  -DgroupId=<groupId> -DartifactId=<artifactId> -Dversion=<version> -Dpackaging=jar -DlocalRepositoryPath=<path_to_lib_dir>
{% endhighlight %}
</li>
<li>Adicione o repositório ao seu POM:
{% highlight xml %}
<repositories>
    <repository>
        <id>lib</id>
        <url>file://${project.basedir}/lib</url>
    </repository>
</repositories>
{% endhighlight %}
</li>
<li>Adicione ao pom as dependências para os jars que você instalou</li>
<li>Felicidade.</li>
</ol>
<p>É isso! Se alguém quiser compartilhar uma solução melhor, fique à vontade.</p>
<!--:-->
