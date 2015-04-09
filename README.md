# annex-test

This is a simple repo to test out git-annex, which is one solution to the
problem of versioning large binary files.  The idea is that the large files
themselves are not stored in git, but symbolic links to the data, as well as
hashes to track changes, and in some cases external links to the data (say in
S3, or on the web via URLs) called "special remotes" are stored in git.  

This repo just demonstrates using URLS as special remotes.   I followed this
[tutorial](https://git-annex.branchable.com/tips/centralized_git_repository_tutorial/)
for setting up a git-annex project in github, with my specific steps listed
below.  You will need to [install](http://git-annex.branchable.com/install/)
git-annex to work with or replicate this project.  Skip steps 3 and 4 if you
are simply using an existing repo like this one that is already setup to work
with git-annex.  

## How to create repo

1.  I created a repo called annex-test in github.

2.  Then I cloned it 

		git clone git@github.com:animetrics/annex-test.git

3.  Then told git-annex to use the repo

		cd annex-test
		git annex init 'my laptop'

4.  Since you can't actually store the contents of the annex files in github, run

		git config remote.origin.annex-ignore true

5.  I created a *beatles* directory and added pictures from the web of John Lennon and Paul McCartney
		mkdir beatles
		cd beatles

		git annex addurl http://blogs.post-gazette.com/2013Scott/John-Lennon.jpg 
		git annex addurl http://assets.rollingstone.com/assets/images/song_review/paulmccartney-624-1382708613-1382734189.jpg 

6.  Now commit

		git commit -am "added john lennon and paul mccartney"
		
7.  And push to the repo.  Note there are 2 branches and they both need to be pushed

		git push origin master git-annex

8.  Again, see [here](https://git-annex.branchable.com/tips/centralized_git_repository_tutorial/) for more details.
		

