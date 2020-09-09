# Bridge for symfony/event-dispatcher-contracts and PSR-14 EventDispatcher

Adapter to provide compatibility with the symfony v4 and v5 event dispatcher contracts with the PSR-14 specification,.


## Installation

```
composer require "typo3/symfony-psr-event-dispatcher-adapter:^1.0 || ^2.0"
```

## Usage

```
use Psr\EventDispatcher\EventDispatcherInterface
use TYPO3\SymfonyPsrEventDispatcherAdapter\EventDispatcherAdapter;

// Use you PSR-14 implementation instead
$dummyPsrEventDispatcher = new class implements EventDispatcherInterface
{
    public function dispatch(object $event) {
       // do something with $event
    }
};

$symfonyEventDispatcher = new SymfonyEventDispatcher($dummyPsrEventDispatcher);

// Usage in symfony components like symfony/mailer
$esmtpTransport = new \Symfony\Component\Mailer\Transport\Smtp\EsmtpTransport(
    $host,
    $port,
    $tls,
    $symfonyEventDispatcher
);
```
