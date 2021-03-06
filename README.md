snhack.github.com
=================

__Note:  master branch is overwritten during compilation.__

This site is built with [octopress] and requires a ruby installation to render the [source branch] to master.

[octopress]: http://octopress.org/docs
[octopress documentation]: http://octopress.org/docs/setup/
[source branch]: https://github.com/snhack/snhack.github.com/tree/source
[fork this repo]: https://github.com/snhack/snhack.github.com/fork_select


### Super minimal way to add a post

If you're submitting a post or edit that uses only standard markdown, you can skip installing octopress and just provide the source.

Browse to the [source/_posts] folder within the source branch of this repo.

[source/_posts]: https://github.com/snhack/snhack.github.com/tree/source/source/_posts

Use github's web interface to [create a new file], [naming it] according to the pattern: ``YYYY-MM-DD-url-safe-title.md``.

[create a new file]: https://github.com/blog/1327-creating-files-on-github
[naming it]: https://github.com/blog/1436-moving-and-renaming-files-on-github

Add [suitable yaml] front matter followed by your content as plain text, as shown in [this example post] \([preview]).  Optionally use \*simple\* [markdown formatting] such as headers, italics and links.  There are [various tools] available to preview standard markdown.

[this example post]: https://raw.github.com/snhack/snhack.github.com/source/source/_posts/_examples/2012-11-06-example-post.md
[preview]: https://github.com/snhack/snhack.github.com/blob/source/source/_posts/_examples/2012-11-06-example-post.md

Commit the new file.  Github will automatically prompt you to submit a pull request to this repo: set the base branch to 'source', review the changes, and hit send.

[suitable yaml]: http://octopress.org/docs/blogging
[markdown formatting]: http://daringfireball.net/projects/markdown/basics
[various tools]: http://daringfireball.net/projects/markdown/dingus



### Install Octopress

When using the extensions provided by octopress or jekyll, or making changes to the site, you should install octopress so you can preview your content before submission.

[Fork this repo], then clone your fork's **source branch** locally.

	git clone -b source git@github.com:<yourusername>/snhack.github.com.git snhack
	cd snhack
	ruby --version  		# Should report Ruby 1.9.3


Install dependencies, ``rake install`` is not required.

	gem install bundler rake
	rbenv rehash			# Only needed with rbenv
	bundle install

If you have any problems, see the [octopress documentation] for more info on installing ruby and other dependencies.



### Adding Content

Create a [new post or page], usually as [markdown].  Use a topic branch if changing the site's source (templates, styles etc.)

	rake new_post["Zombie Ninjas Attack"]
	# Creates source/_posts/2011-07-03-zombie-ninjas-attack.md

[new post or page]: http://octopress.org/docs/blogging
[markdown]: http://daringfireball.net/projects/markdown


Edit the new post with your favourite text editor.

	nano source/_posts/2011-07-03-zombie-ninjas-attack.md


Generate and preview your changes locally at ``http://localhost:4000``.

	rake generate   # Generates posts and pages into the public directory
	rake preview	# Watches, and mounts a webserver at http://localhost:4000


Commit changes to your fork, then submit a pull request to this repo.

Once your changes are accepted, an admin will need to generate the site using ``rake deploy`` before they become live.
