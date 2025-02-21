# cv-akim
CV latex template that I am using.

## 1. Organization

1) Two tex files are the main `cv.tex` and `resume.tex`.

2) `*.sty` files define acronym used in the cv. Add your own acronym here.

3) `src` folder contains each module. You can add or remove provided module here. Once you add or remove go to `cv.tex` or `resume.tex` and adjust `\input{*.tex}` list.

4) Reference is handled in `src\ref.bib`. Add your bib item here and use it from `pubs.tex` by calling the bibkey. For example

```
\item \bibentry{ycho-2017-icra}
```

5) Yet I could not figure out how to make it work with Korean bib items in a bib file.

한국어 bib아이템은 bib파일 안에 들어가면 이상하게 깨지는데 아직 원인을 찾지 못함. `pubs.tex`내에 한국어 bibitem은 따로 관리하는 중.

## 2. Compile

Run the following command

```
pdflatex cv.tex  
bibtex cv.tex  
pdflatex cv.tex  
pdflatex cv.tex  
```
You may encounter the following error on the first time compile. Just repeat the `pdflatex`.

```
...and\NAT@force@numbers{}\NAT@force@numbers
```

## 3. Korean CV

cv.tex에 kor_only 라는 boolean 이 있어서 `true` 로 만들면 한글버전일때만 특정 라인을 보이게 할 수 있음. 
```
\setboolean{kor}{false}
```

## 4. Privatization of the partial CV

By cloning this public repo and adding remote, you can partially privatize the cv.

https://stackoverflow.com/questions/7983204/having-a-private-branch-of-a-public-repo-on-github

Make a private repo. For example, `cv-akim-confidential`.

```
git clone --bare https://ayoungk@github.com/ayoungk/cv-akim.git
cd cv-akim
git push --mirror  https://ayoungk@github.com/ayoungk/cv-akim-confidential.git
```

Then clone this private clone `cv-akim-confidential` and add remote
```
git remote add public  https://ayoungk@github.com/ayoungk/cv-akim.git
```
