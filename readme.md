Simple declarative command line interface specification via structs for go libraries. This was primarily developed as a tool for a proof-of-concept CLI generator (github.com/jnathanh/go-generate-cli).

It does not currently support CLI documentation. It pre-parses and validates command line arguments of type string, bool, int, and float. It supported order-dependent arguments and flags. It automatically outputs the handler's returned value to STDOUT.

```golang
	spec := cli.Spec{
		Params: []cli.Value{
			{Name: "name", TypeName: "string", Ordered: true},
		},
		Handler: func(inputs cli.Inputs) (output interface{}, err error) {

			name := inputs.Named["name"].(string)

			return "hello " + name, nil
		},
	}
    c := cli.New(spec)
    c.ExecOSArgs()

    // example usage:
    // $ greet John
    // $ hello John
```
