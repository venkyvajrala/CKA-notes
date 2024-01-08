

 
 ```yaml
 containers:
	 - name:
	   image:
	   command: [“”] # entrypoint overide
	   args: [“”] -> # CMD overide
```


k run nginx —image=nginx —dry-run=client -o yaml -- —color red 

k run nginx —image=nginx —dry-run=client -o yaml —command python app.py — color red