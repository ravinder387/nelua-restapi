# nelua-restapi
[Nelua](https://nelua.io/) is a compiled programming language which compile to c code and exe file. The syntax is almost similar to lua but with type<br>
annotations. I used mongoose and cJSON's nelua wrapper which is c library.<br>

### Step-1 compile the program
First make sure you have installed nelua then<br>
```{nelua}
nelua json.nelua
```
Run<br>
In linux:- ./json<br>
In windows:- .\json.exe<br>

### Step-2 Call from R
```{r}
library(httr)
library(jsonlite)

url <- "http://localhost:8000/api/mean"

l <- list(data = rnorm(c(1,2,3)))
j <- toJSON(l)

# post request
req <- POST(url, body = j
              , encode = "json")

# response
res <- content(req, type = "text", encoding = "UTF-8")
res <- fromJSON(res)
res$result
```
