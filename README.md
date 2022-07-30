# webcad


```go
package main

import (

)

func main() {
    

url := constants.WebCadMontcoPrint
	r, err := Get(url)
	if err != nil {
		t.Fatalf("err: %s\n", err)
	}

	util.WriteString("mainPage", r, 0644)

	station, incident, err := Tag(r)
	if err != nil {
		t.FailNow()
	}
}