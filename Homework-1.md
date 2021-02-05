HW1
================
Junhan Huang

# 1.Bridge

``` r
CA19<-read.delim("~/Desktop/CA199.txt")
```

# 2.Faculty

``` r
Name<-c()
Position<-c()
Department<-c()
Degree_Information<-c()

Faculty<-read_html("https://guide.wisc.edu/faculty/")

Faculty_text<-Faculty %>% 
    html_nodes("ul.uw-people")%>%
  html_nodes("li")

n<-length(Faculty_text)

for(i in 1:n){
  FT<-html_node(Faculty_text[i], "p")
  FT<-as.character(FT)
  FT<-gsub("<p>", "", FT)
  FT<-gsub("</p>", "", FT)
  FT<-strsplit(FT, "<br>")
  INF<-unlist(FT)
  Name[i]<-INF[1]
  Position[i]<-INF[2]
  Department[i]<-INF[3]
  Degree_Information[i] <- INF[4]
}
Faculty_Text <- data.frame(Name, Position, Department, Degree_Information)
```
