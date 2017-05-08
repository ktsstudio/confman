# Confman

Library for configuration application

## Usage

##### settings.py

```python
import os
from confman import define, options

define('debug', default=False, type=bool, help='debug')
define('listen', type=dict, default={
    'host': '127.0.0.1',
    'port': 5555,
}) 

CONF = os.getenv('CONF', '/etc/app/app.yaml')
if os.path.exists(CONF):
    options.read_config(CONF)

```

##### /etc/app/app.yaml
```yaml
listen:
    port: 9000
```

##### main.py
```python
from settings import options
print(options.broker)
print(options.broker['port'])
```

##### Output:
```
{'host': '127.0.0.1', 'port': 9000}
9000
```
