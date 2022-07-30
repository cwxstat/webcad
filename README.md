# webcad



```go
package main

import (
	"fmt"

	"github.com/cwxstat/webcad/constants"
	"github.com/cwxstat/webcad/scrape"
)

func main() {
	url := constants.WebCadMontcoPrint
	r, err := scrape.Get(url)
	if err != nil {
		fmt.Println(err)
		return
	}
	station, incident, err := scrape.Tag(r)
	if err != nil {
		fmt.Println(err)
		return
	}
	for i, l := range incident {
		r, err = scrape.Get(scrape.GetDetail(l))
		if err != nil {
			fmt.Println(err)
			return
		}
		if len(station) <= i {
			fmt.Printf("station: %v, incident: %v\n", "none", l)
		} else {

			fmt.Printf("station: %v, incident: %v\n", station[i], l)
		}

	}

}


```
