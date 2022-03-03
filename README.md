# typed_argument_parser

An abstract base class that provides the `argparse.Namespace` returned by `ArgumentParser.parse_args` with field and type information. This enables Python IDEs to be more helpful. An exception is raised if fields not defined are attempted to be assigned the namespace.

## Usage

Define a argument parser class that inherits `TypedArgumentParser`:

```python
from typed_argument_parser import TypedArgumentParser

class PublicSuffixArgumentParser(TypedArgumentParser):
    ...
```

Define a class within the argument parser class that specifies the resulting fields and types from calling `parse_args` on the class instance:

```python
class PublicSuffixArgumentParser(TypedArgumentParser):

    class Namespace:
        domain_names: set[str]
        list_file_path: Optional[TextIOWrapper]
        json: bool
```

Call `parse_args`, with the type of resulting namespace specified:

```python
args: Type[PublicSuffixArgumentParser.Namespace] = PublicSuffixArgumentParser().parse_args()
```

Be provided with completions and erroneous usage information by your Python IDE!

(insert pictures)

👍
