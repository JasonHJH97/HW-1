HW1
================

# 1.Bridge

``` r
CA19<-read.delim("~/Desktop/CA199.txt")
```

# 2.Faculty

``` r
Faculty<-read_html("https://guide.wisc.edu/faculty/")
Faculty_text <- Faculty %>% 
    html_nodes("p") %>% 
    html_text()
FACULTY<-tibble(Faculty_text)
FACULTY<-FACULTY[-c(1,2),]
FACULTY<-FACULTY[-3989,]



FF<-readLines("https://guide.wisc.edu/faculty/")
FF<-tibble(FF)
A<-FF[c(163:188),1]
A<-unlist(A)
A<-strsplit(A,split="<br/></p></li><li><p")
A<-unlist(A)
A<-strsplit(A,split="<ul class=\"uw-people\"><li><p>")
A<-tibble(A)
A<-unlist(A)
A<-strsplit(A,split="<br/>")
A<-unlist(A)
A<-tibble(A)

name_num<-seq(from=1, to=15918, by=4)
position_num<-seq(from=2, to=15918, by=4)
department_num<-seq(from=3, to=15918, by=4)
degree_information_num<-seq(from=4, to=15918, by=4)
```
