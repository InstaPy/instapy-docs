# Welcome to InstaPy's FAQ!

## You're probably here because you ran into a known problem, so let's start with a checklist to make sure everything is installed:

Remember: I'll refer to the `python` and `pip` version you want to run `InstaPy` with (because some users have multiple python instances which lead to different aliases) as follows:
`python` = your `python` alias, e.g. `python2`, `python3`, `python3.x`, `python3x` etc.

### 1. Is InstaPy installed?

```python
python -m pip show instapy
```

<details><summary>It's not installed?(If there's no output):mag_right:</summary>Install it with

```python
python -m pip install instapy

```

</details>

### 2. Is your installation up-to-date?

Look at [PyPi](https://pypi.org/project/instapy/#history) and compare it to the version `python -m pip show instapy` showed you.
<details><summary>It's not up-to-date?:mag_right:</summary>Update InstaPy: <details><summary><code>Git</code> installation :mag_right:</summary>Use

```bash

git pull

```

inside of the folder you cloned from GitHub.</details><details><summary><code>Pip </code> installation:mag_right:</summary>Use

```bash

pip install instapy -U

```

to update the package.</details> don't mix the two installations up except you know *exactly* what you're doing.</details>

<details><summary><h3> 3. Do you have Chrome and Chromedriver installed? Are they compatible?:mag_right:</h3></summary>

#### 3.1 Check Chrome's version:

<details><summary>Mac:mag_right:</summary>Search for Chrome with Spotlight search, or just open it if you have a shortcut.Then open the menu -> Help -> About Chrome.</details>
<details><summary>Windows:mag_right:</summary>On Windows you can search for Chrome from the Start-Menu(the menu that comes when you press the windws-key or click the Windows logo in the bottom-left corner, or just open it if you have a shortcut.Then open the menu -> Help -> About Chrome. </details>
<details><summary>Linux Debian Distros (e.g. Raspbian, Ubuntu, Kali etc.):mag_right:</summary>On Linux Debian Distros you can run

```bash
chromium-browser --version
```

<details><summary>Command can't be found?:mag_right:</summary>
If <code>chromium-browser</code> can't be found, install it via

```bash
sudo apt-get install chromium-browser
```

And if tis still can't be found, use

```bash
sudo apt install chromium-browser
```

</details>
</summary>
</details>

#### 3.2 Check the driver's version:

<details><summary>You're using InstaPy's built-in Chromedriver? :mag_right:</summary> Check the version with

```bash
python -m pip show instapy-chromedriver
```

</details>
<details><summary>You're not?:mag_right:</summary>
TODO
</details>

#### 3.3 Now: Check whether your Chrome and Chromedriver are compatible:

<table>
<thead>
<th>chromedriver</th>
<th>chrome</th>
</thead>
<tbody>
<tr><td>2.46</td><td>71-73</td></tr>
<tr><td>2.45</td><td>70-72</td><tr>
<tr><td>2.44</td><td>69-71</td><tr>
<tr><td>2.43</td><td>69-71</td><tr>
<tr><td>2.42</td><td>68-70</td><tr>
<tr><td>2.41</td><td>67-69</td><tr>
<tr><td>2.40</td><td>66-68</td><tr>
<tr><td>2.39</td><td>66-68</td><tr>
<tr><td>2.38</td><td>65-67</td><tr>
<tr><td>2.37</td><td>64-66</td><tr>
<tr><td>2.36</td><td>63-65</td><tr>
<tr><td>2.35</td><td>62-64</td><tr>
<tr><td>2.34</td><td>61-63</td><tr>
<tr><td>2.33</td><td>60-62</td><tr>
<tr><td>2.28</td><td>57+</td><tr>
<tr><td>2.25</td><td>54+</td><tr>
<tr><td>2.24</td><td>53+</td><tr>
<tr><td>2.22</td><td>51+</td><tr>
<tr><td>2.19</td><td>44+</td><tr>
<tr><td>2.15</td><td>42+</td><tr>
</tbody>
</table>
<details><summary>They're not compatible?:mag_right:</summary> Download a compatible chromedriver by using

```python
python -m pip uninstall instapy-chromedriver
python -m pip install instapy-chromedriver==desiredversion
```
and delete the Chromedriver executable in <code>InstaPy/assets</code>, if you had one
</details></details></details>

<details><summary><h3> 3. Do you have Firefox and Geckodriver installed? Are they compatible?:mag_right:</h3></summary>

#### 3.1 Check the Firefox's version:

<details><summary>Mac:mag_right:</summary>Search for Firefox with Spotlight search, or just open it if you have a shortcut. Then open the menu -> Help -> About Firefox.</details>
<details><summary>Windows:mag_right:</summary>On Windows you can search for Firefox from the Start-Menu(the menu that comes when you press the windws-key or click the Windows logo in the bottom-left corner, or just open it if you have a shortcut.Then open the menu -> Help -> About Firefox. </details>
<details><summary>Linux Debian Distros (e.g. Raspbian, Ubuntu, Kali etc.):mag_right:</summary>On Linux Debian Distros you can run

```bash
firefox --version
```

<details><summary>Command can't be found?:mag_right:</summary>
If <code>firefox</code> can't be found, install it via

```bash
sudo apt-get install firefox
```

And if this still can't be found, use

```bash
sudo apt install firefox
```

</details>
</details>

#### 3.2 Check the driver's version:

TODO

#### 3.3 Now: Check whether your Firefox and Geckodriver are compatible:

<img src="https://i.stack.imgur.com/vRK7K.png" alt="Firefox and Geckodriver versions"><details><summary>They're not compatible?:mag_right:</summary> Download a compatible Geckodriver from here: <a href="https://github.com/mozilla/geckodriver/releases">Geckodriver releases</a></details></details>

## Now, that we can be sure everything is installed correctly and that hasn't fixed your issue, let's get to troubleshooting:

**PLEASE FIRST READ WHAT THE ERROR OUTPUT SAYS, THINK ABOUT WHAT IT COULD MEAN AND HOW YOU COULD FIX IT**

<details><summary> OSError: [Errno 8] Exec format error:mag_right: </summary>

Make sure your chromedriver is the correct bit-version for your system, you're probably on Raspberry if you encountered this issue.
To install the chromedriver that fits the Raspberry's ARM-structure, run

```bash
pip3 install --user instapy-chromedriver==2.36.post0
```

</details>

<details><summary> No module named "xy":mag_right: </summary>

Make sure the python instance you used to execute your InstaPy script has all dependencies and the `instapy` package installed.</details>

More issues will be added in the future. For further questions: there's almost always someone online on the Discord server.

Written by @TarekJ03