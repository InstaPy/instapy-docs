## Creating a release

### Travis CI deploy to PyPI on tags (<i>2 in 1</i> ☕)
    
**1**. _Change_ the _**version number**_ in the `__version__` variable at **__init__.py** file inside **instapy** package [folder] to the _**new**_ version number (follow [SemVer](https://semver.org)).

E.g. for a bug fix:
```python
__version__ = "0.1.5" # <= from 0.1.4
```

**2**. `add` and `commit` the change made to **__init__.py** regarding version increment and `push` it..
```yaml
git add .
git commit -m "new bug fix version: 0.1.5"
git push   # you don't have to push, but it would be better
```

**3**. Make _**a new** git_ _**tag**_ with the _exact_ version number you have just set in the 1st step,
```yaml
git tag 0.1.5
```

**4**. _**Push**_ that _**new tag**_
```yaml
git push --tags
```

**5**. **Ta Da** 🎉
Github will make a new release by that tag and send a request to Travis CI that "_Hey bro, I've just received a new tag!_" and Travis CI will immidiately check,  

But if all those above are true, then Travis CI will start building the jobs at all of the three stages available- _static analysis_, _test_ and then _deploy to PyPI_ automatically with the version you have set in `__version__` variable at **__init__.py** file included in the freshly tagged release.

---

### Advice
Before incrementing the `__version__` at **__init__.py** and tagging that same version with git to push tags, make sure your code works really good and the build with the same code has passed before.  
I mean do anything you can merge PRs or git push locally and see that build has passed.  
And only then, increment the version number and make a new tag with that new version and push that tag.  
It will make sure your build will surely pass and deployment will _succeed_ **always** 🎉

---

### Bad Situation
You push a tag to Github which ends up failing at _static analysis_ or _test_ stage and obviously - not being deployed to PyPI.  
At that point, you will end up with a new release at Github and not having that release deployed to PyPI 😥

**a**-) You can either push new commits to Github which will solve those problems and you build passes at Travis CI so that you are ready to deploy to PyPI.  
Then make the distribution files manually and upload that to PyPI by hand.  
Which will have your Github and PyPI stay at the same version in parallel.  
  
**b**-) You can first delete the release at Github (_it allows readding releases_) and then push the commits which will solve problems and have Travis CI build pass and are ready to deploy.  
Then make that release tag again and push it to Github once again.  
It will make a new Github release and also, obviously, pass static _analysis_ & _test_ stages and deploy to PyPI successfully.
