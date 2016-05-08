# panorama  
**This is my private git repository for cs281b**  
![img](https://github.com/yihui-he/panorama/blob/master/results/intersection.jpg)  
![img](https://github.com/yihui-he/panorama/blob/master/results/GrandCanyon2.jpg)  
![img](https://github.com/yihui-he/panorama/blob/master/results/redrock.jpg)  
### bonus  
I implemented all of the elaborate features described in **BONUS** part.  
- I'm able to handle 360 panorama.
- Random sequence of images input is welcomed.
- I use color blending and smoothing to make the image more continuous.  

### how to run  
images sets are already in ./imgs  
- If you want to see results directly, go to ./results folder
- If you want to test all images sets with only one click,run RunAllDatasets.m.(This may run 1 or more minutes)  
- If you want to specify the image folder, run main.m with path to images folder as argument(as described in assignment)  

**Note that**, if you use the last way to run my code, the folder names should be as follows(I need to tune focus on each image set)  
'ucsb4','family_house','glacier4','yellowstone2','GrandCanyon1','yellowstone5','yellowstone4','west_campus1','redrock','intersection','GrandCanyon2'  
For example:  
`main('./imgs/ucsb4/');`

######details of my algorithms are shown below:  

### 360 panorama
- [x] mapping image to cylindrical coordinate  
*warp.m*  

### recognize panorama(random inputs)
I select two random sequence images set:family\_house, and west\_campus1  
They are already shuffled. You can see them in imgs folder.  
Or you can run shuffle.bash to shuffle them again.  
As described in Brown's paper, I use $N\_inlier>k\*N\_pairs+b$ to compute whether a pair of images match or not  
k,b are const. Set to 5.9 and 0.22 respectively.  
See [recognizing panorama](https://github.com/yihui-he/panorama/blob/master/resource/recognizing_panorama.pdf) for details  

*imorder.m*  

### merging and blending  
- [x] Alpha  
- [ ] Pyramid  
- [x] Noblend

*merge.m*  

### transformation
- [x] homography transformation.
- [x] translation transformation.( This is more robust)

*computeTrans.m*  

### matching
- [x] RANSAC
- [ ] exposure matching  

*RANSAC.m*  

### global adjustment
- [x] end to end adjustment(comput shift and subtract shift/n to each image)  
- [ ] bundle adjustment(difficult way)  

*create.m*  

### getting features
- [x] use SIFT features(using VLFeat library, professor allowed)  
- [x] SURF features, (SIFT is better)  

*getSIFTFeatures.m, getMatches.m*  
  
### resize  
- [x] I resize image larger than 400 pixel in width  
  
*main.m*  
  
### References  
[A nice tutorial](https://github.com/yihui-he/panorama/blob/master/resource/stitching%20tutorial.pdf) on panorama I find useful.  

