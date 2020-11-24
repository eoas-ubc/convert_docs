# converting docx, tex and pptx to markdown

## docx

`conda install pandoc`

Then to convert to "github flavored markdown (gfm)" saving all figures in a folder called "media" in the current directory.

```
pandoc --to gfm --extract-media='.' week01WS01.docx -o week01S01.md
```

The result:  [week01S01.md](week01WS01.md)


Issues

1) figures need to be included with `<img>` tags and sized correctly.
2) Tables unlikely to render correctly
3) superscripts and subscripts need editing (I have a regular expression filter for that)

## pptx

### Step 1: extract the images to a folder named media

```
export cdocs=~/repos/convert_docs
cd $cdocs
conda install conda-lock
conda-lock -f environment.yml -p osx-64
conda  create --name convert  --file conda-osx-64.lock
conda activate convert
cd ~/google_drive/e340_convert/Day_01_Intro/Slides
python $cdocs/scripts/image_extract.py Day01_IntroClass_2019t2.pptx media
```

### Step 2: convert any wmf files to png using snaggit

### Step 3: make the markdown file

`python $cdocs/scripts/build_notebook.py Day01_IntroClass_2019t2.pptx media`

### Step 4: edit the markdown to make questions md2canvas compatible



