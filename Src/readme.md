# Comparing Two JSON Objects irrespective of order  ![CI status](https://img.shields.io/badge/build-passing-brightgreen.svg)

## Installation

### Requirements
* Python 3.3 and up

`$ pip install foobar`

`$ git clone `

## Code

```python
__version__='1.0.0'
__Author__='rajesh_alonea'

import json
from jsondiff import diff

class JsonTest():

    def ordered(self,obj):
        if isinstance(obj, dict):
            return sorted((k, self.ordered(v)) for k, v in obj.items())
        if isinstance(obj, list):
            return sorted(self.ordered(x) for x in obj)
        else:
            return obj

    @staticmethod
    def comparejson(obj1,obj2):
        return diff(obj1,obj2)



if(__name__=='__main__'):
        ls = JsonTest()
        with open('data.json') as json_data_patch:
            Jobj = json.load(json_data_patch)
            Obj = ls.ordered(Jobj)
        with open('data1.json') as json_data_1:
            Jobj2 = json.load(json_data_1)
            Obj2 = ls.ordered(Jobj2)

            print(Obj)
            print("the given Json Files are",ls.comparejson(Obj,Obj2))



```

## Development
```
$ pip install -e
```

## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License
[MIT]()