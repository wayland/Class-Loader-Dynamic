# Class::Loader::Dynamic

Will dynamically create classes with the same name as the modules.  Modules can be specified with the glob language.

```
use	Class::Loader::Dynamic;

class Foo does Class::Loader::Dynamic {}

my $loader = Foo.new();
my ($passes, $fails) = $loader.load-module-pattern(
	:paths(['lib', 't']),
	:globs(["Lo?derTest*"]),
);
$passing-class = $passes<LoaderTestPassing>
$passing-class.the-method()
```
The above code will try to load eg. `LoaderTestPassing` and `LoaderTestFailing`, and even `LoZderTestZZZZZ`,
but will ignore `IgnoreLoaderTest`.  

It will also call `.the-method` on the new object that's a `LoaderTestPassing`.
