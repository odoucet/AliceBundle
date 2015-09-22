# Alice Processors

Refer to [nelmio/alice](https://github.com/nelmio/alice/blob/master/doc/processors.md#processors) documentation to see how to create a Processor
class. Given you declared a processor `AppBundle\DataFixtures\Processor\UserProcessor`, you have to declare it as a
service with the tag `hautelook_alice.alice.processor` to register it:

```yaml
# app/config/services.yml

services:
    alice.processor.user:
        class: AppBundle\DataFixtures\Processor\UserProcessor
        tags: [ { name: hautelook_alice.alice.processor } ]
```

You can also overload getProcessors() in your TestLoader class this way : 
```php
    // file MyBundle\DataFixtures\ORM\TestLoader.php
    
    public function getProcessors()
    {
        return [
            new AppBundle\DataFixtures\Processor\UserProcessor($this->container),
        ];
    }

```

Previous chapter: [Custom Faker providers](faker-providers.md)<br />
Next chapter: [DoctrineFixturesBundle support](doctrine-fixtures-bundle.md)
