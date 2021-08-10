# README file for deploying blog. 

## Python environment: 
- conda environment: blog

## Build test deploy:
build: `ablog build`
test: `ablog serve`
deploy: git commit `website_`, push. 

## Organization:
All files with the "post" directive will be included in the blog. We have created three categories of post, for Literature Review (Lit), Research Ideas (Res), and Project Documentation (Doc). Each has its own folder `Literature`, `Research`, `Documentation` where we keep the ".rst" files for that particular kind of post. 

## Resources: 
Working example: https://predictablynoisy.com/posts/2020/sphinx-blogging/
Ablog: https://ablog.readthedocs.io/en/latest/
sphinxcontrib-bibtex: https://sphinxcontrib-bibtex.readthedocs.io/en/latest/usage.html


