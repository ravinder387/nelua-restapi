# nelua-restapi
[Nelua](https://nelua.io/) is a compiled programming language which compile to c code and exe file. The syntax is almost similar to lua but with type
annotations.<br> I used mongoose and cJSON's nelua wrapper which is c library.<br>

### Step-1 compile the program
First make sure you have installed nelua then<br>
```{nelua}
nelua json.nelua  -- it directly run the server
```
Run the exe file if you want<br>
It compiled and save c code and exe file inside cache directory of your system<br>
In linux:- ./json<br>
In windows:- .\json.exe<br>

### Step-2 Call from R
```{r}
library(httr)
library(jsonlite)

url <- "http://localhost:8000/api/mean"

l <- list(data = c(1,2,3))  # Note - vector size must be <= 400000
j <- toJSON(l)

# post request
req <- POST(url, body = j
              , encode = "json")

# response
res <- content(req, type = "text", encoding = "UTF-8")
res <- fromJSON(res)
res$result
```
