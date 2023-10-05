---
title: "Pruebas de integración - Introducción"
date: 2023-10-05
categorias: [ "Testing" ]
autores: [ "Manuel Cánepa" ]
tags: [ "testing" ]
description: "Introducción a las pruebas unitarias como parte de las buenas prácticas."
---

Antes de arrancar con las pruebas, es necesario configurar el entorno. Lo primero es crear la base de datos donde se
ejecutaran los test, tengan en cuenta que se usa un entorno Magento, pero lo mismo aplica para cualquier proyecto que
implemente pruebas unitarias.

```shell
$ warden db connect -uroot
MariaDB [magento]> CREATE DATABASE magento_integration_tests;
MariaDB [magento]> GRANT ALL ON magento_integration_tests.* TO 'magento_test'@'%' IDENTIFIED BY 'magento';
```

Ejecutando esas lineas desde el directorio principal del proyecto se crea la base de datos magento_integration_tests y
se le otorga permisos al usuario magento_test.

Para poder configurar el uso de esta nueva base de datos se debe generar el siguiente archivo:

`dev/tests/integration/etc/install-config-mysql.php:`

```php
<?php

return [
    'db-host' => 'db',
    'db-user' => 'magento_test',
    'db-password' => 'magento',
    'db-name' => 'magento_integration_tests',
    'db-prefix' => '',
    'backend-frontname' => 'backend',
    'search-engine' => 'elasticsearch7',
    'elasticsearch-host' => 'elasticsearch',
    'elasticsearch-port' => 9200,
    'admin-user' => \Magento\TestFramework\Bootstrap::ADMIN_NAME,
    'admin-password' => \Magento\TestFramework\Bootstrap::ADMIN_PASSWORD,
    'admin-email' => \Magento\TestFramework\Bootstrap::ADMIN_EMAIL,
    'admin-firstname' => \Magento\TestFramework\Bootstrap::ADMIN_FIRSTNAME,
    'admin-lastname' => \Magento\TestFramework\Bootstrap::ADMIN_LASTNAME,
    'amqp-host' => 'rabbitmq',
    'amqp-port' => '5672',
    'amqp-user' => 'guest',
    'amqp-password' => 'guest',
];
```

Luego de esto, si es necesario agregar configuraciones especificas para el correcto funcionamiento de los módulos a
testear, se deben guardar en el siguiente archivo:

`dev/tests/integration/etc/config-global.php:`

```php
<?php
// Ejemplo: 
return [
    'customer/password/limit_password_reset_requests_method' => 0,
    'admin/security/admin_account_sharing' => 1,
    'admin/security/limit_password_reset_requests_method' => 0,
    'some/custom/path' => 'some-custom-value'
];
```

Estas configuraciones serán globales, en caso de que algún test requiera una configuración particular se podrá usar la
annotation @magentoConfigFixture

Para ejecutar test, en mi caso para el proyecto de Tango, copie el archivo dev/tests/integration/phpunit.xml.dist en
dev/tests/integration/phpunit.xml y agregue las siguientes lineas:

```xml

<testsuite name="Gento Integration Tests">
        <directory>../../../vendor/gento-arg/module-*/src/Test/Integration</directory>
    </testsuite>
```

De esa forma puedo ejecutar lo siguiente para correr los test de integracion:

```shell
$ warden env shell
$ cd dev/tests/integration
$ php ../../../vendor/bin/phpunit --testsuite 'Gento Integration Tests'
```

Al ejecutar ese comando, va a ocurrir un error si es que hay algun problema de dependencias ya que las tablas no se
instalaran. Primero hay que validar que todas las dependencias de los modulos sean correctas en los
archivos `etc/module.xml` de cada modulo.

Si despues de eso, sigue dando error (como fue mi caso), puede que haga falta deshabilitar algún módulo durante la
instalación y luego volver a habilitarlo. Para ello, podemos correr el script de instalacion que se podrá ver como parte
del error que arroje el comando anterior, por ejemplo:

```shell
Next Magento\Framework\Exception\LocalizedException: Command returned non-zero exit code:
`/usr/bin/php -f '/var/www/html/bin/magento' setup:install -vvv --db-host='db' \
              --db-user='magento_test' --db-password='magento' --db-name='magento_integration_tests' \
              --db-prefix='' --backend-frontname='backend' --search-engine='elasticsearch7' \
              --elasticsearch-host='elasticsearch' --elasticsearch-port='9200' --admin-user='user' \
              --admin-password='password1' --admin-email='admin@example.com' \
              --admin-firstname='firstname' --admin-lastname='lastname' --amqp-host='rabbitmq' \
              --amqp-port='5672' --amqp-user='guest' --amqp-password='guest' \
              --magento-init-params='MAGE_DIRS[etc][path]=/var/www/html/dev/tests/integration/tmp/sandbox-0-5c5a8a53947b9d438b48a3d1262ca4dfbbb7ae316d162990e13dabb483882f99/etc&MAGE_DIRS[var][path]=/var/www/html/dev/tests/integration/tmp/sandbox-0-5c5a8a53947b9d438b48a3d1262ca4dfbbb7ae316d162990e13dabb483882f99/var&MAGE_DIRS[var_export][path]=/var/www/html/dev/tests/integration/tmp/sandbox-0-5c5a8a53947b9d438b48a3d1262ca4dfbbb7ae316d162990e13dabb483882f99/var/export&MAGE_DIRS[media][path]=/var/www/html/dev/tests/integration/tmp/sandbox-0-5c5a8a53947b9d438b48a3d1262ca4dfbbb7ae316d162990e13dabb483882f99/pub/media&MAGE_DIRS[static][path]=/var/www/html/dev/tests/integration/tmp/sandbox-0-5c5a8a53947b9d438b48a3d1262ca4dfbbb7ae316d162990e13dabb483882f99/pub/static&MAGE_DIRS[view_preprocessed][path]=/var/www/html/dev/tests/integration/tmp/sandbox-0-5c5a8a53947b9d438b48a3d1262ca4dfbbb7ae316d162990e13dabb483882f99/var/view_preprocessed/pub/static&MAGE_DIRS[code][path]=/var/www/html/dev/tests/integration/tmp/sandbox-0-5c5a8a53947b9d438b48a3d1262ca4dfbbb7ae316d162990e13dabb483882f99/generated/code&MAGE_DIRS[cache][path]=/var/www/html/dev/tests/integration/tmp/sandbox-0-5c5a8a53947b9d438b48a3d1262ca4dfbbb7ae316d162990e13dabb483882f99/var/cache&MAGE_DIRS[log][path]=/var/www/html/dev/tests/integration/tmp/sandbox-0-5c5a8a53947b9d438b48a3d1262ca4dfbbb7ae316d162990e13dabb483882f99/var/log&MAGE_DIRS[session][path]=/var/www/html/dev/tests/integration/tmp/sandbox-0-5c5a8a53947b9d438b48a3d1262ca4dfbbb7ae316d162990e13dabb483882f99/var/session&MAGE_DIRS[tmp][path]=/var/www/html/dev/tests/integration/tmp/sandbox-0-5c5a8a53947b9d438b48a3d1262ca4dfbbb7ae316d162990e13dabb483882f99/var/tmp&MAGE_DIRS[upload][path]=/var/www/html/dev/tests/integration/tmp/sandbox-0-5c5a8a53947b9d438b48a3d1262ca4dfbbb7ae316d162990e13dabb483882f99/var/upload&MAGE_DIRS[pub][path]=/var/www/html/dev/tests/integration/tmp/sandbox-0-5c5a8a53947b9d438b48a3d1262ca4dfbbb7ae316d162990e13dabb483882f99/pub&MAGE_DIRS[import_export][path]=/var/www/html/dev/tests/integration/tmp/sandbox-0-5c5a8a53947b9d438b48a3d1262ca4dfbbb7ae316d162990e13dabb483882f99/var&MAGE_MODE=developer'
            2>&1` in /var/www/html/vendor/magento/framework/Shell.php:66
```

De ese error, extraemos el comando para instalar y agregamos el parametro --disable-modules y agregamos cada modulo
separado por coma, por ejemplo los de Mageplaza:

```shell
bin/magento setup:install [...] --disable-modules='Mageplaza_Core,Mageplaza_Smtp'
```

En el caso de Mageplaza ocurre un error conocido que resulta de intentar crear un schema ANTES que ocurran los data y
por ende que la entidad customer no exista. Para los modulos desarrollados por nosotros podemos usar un Proxy como
indica el siguiente [comentario](https://github.com/magento/magento2/issues/34220#issuecomment-932183698). Si dentro del
archivo phpunit.xml está habilitada la opción de TESTS_CLEANUP, los módulos deben ser desactivados por configuracion
para que cada vez que se instale la base de datos, esos módulos no sean tenidos en cuenta, pero con esta combinación no
podremos realizar test unitarios sobre dichos módulos.

Luego de corregir todo lo que tengamos que corregir, se deberia poder ejecutar el comando de tests con un resultado
similar al siguiente:

```shell
www-data@magento-php-debug:/var/www/html/dev/tests/integration$ php ../../../vendor/bin/phpunit --testsuite 'Gento Integration Tests'
PHPUnit 9.2.6 by Sebastian Bergmann and contributors.

Warning:       Using a custom test suite loader is deprecated

No tests executed!

=== Memory Usage System Stats ===
Memory usage (OS):	133.16M (172.93% of 77.00M reported by PHP)
Estimated memory leak:	56.16M (42.17% of used memory)
```

En este caso, no hay test de integracion que se hayan ejecutado.

Otra forma de ejecutar los tests de integración es ejecutando desde el directorio principal del proyecto lo siguiente:

```shell
$ vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml --testsuite 'Gento Integration Tests'
```

Para crear el primer test, y siempre basandonos en la configuración realizada previamente, es necesario crear la ruta
Test/Integration dentro del directorio del módulo que creamos conveniente.

Para poder realizar los test de integración, la mayoria de las veces es necesario que haya datos cargados, para eso
Magento provee annotation como es el caso de @magentoDataFixture, esto permite crear un unico archivo php donde se
carguen los datos y ese mismo archivo pueda ser utilizado en varios métodos, incluso pueda ser llamado y requerido de
otros módulos.

Un ejemplo sería dar de alta algunos productos para poder realizar operaciones con ellos. En el siguiente ejemplo se dan
de alta productos en un schema, y pedidos en otro. Estos datos son cargados en la base de datos, pero Magento encapsula
todas las consultas dentro de una transacción y luego de la ejecución hace rollback, de esta forma, los datos estarán
disponibles para su uso, pero inmediatamente después de que el test sea ejecutado se revierte el dato para que las
tablas se mantengan lo mas limpias posible:

`vendor/gento-arg/module-tango-tiendas/src/Test/Integration/Service/OrderSenderServiceTest.php:`

```php 
<?php

namespace Gento\TangoTiendas\Test\Integration\Service;

class OrderSenderServiceTest extends \PHPUnit\Framework\TestCase
{
    /**
     * @magentoDataFixture Gento_TangoTiendas::Test/_files/product_list.php
     * @magentoDataFixture Gento_TangoTiendas::Test/_files/orders_to_publish.php
     * @return void
     */
    public function testSuccessfullyPublishOrder(): void
    {
        // Dentro de este método se podrán obtener los datos guardados en esos dos archivos
```

Para generar estos archivos simplemente se deben crear y escribir lo necesario para generar los datos en base de datos:

`vendor/gento-arg/module-tango-tiendas/src/Test/_files/product_list.php:`

```php
<?php

use Magento\Catalog\Api\Data\ProductInterfaceFactory;
use Magento\Catalog\Api\ProductRepositoryInterface;
use Magento\Catalog\Model\Product\Attribute\Source\Status;
use Magento\Catalog\Model\Product\Type;
use Magento\Framework\Api\SearchCriteriaBuilder;
use Magento\TestFramework\Helper\Bootstrap;
use Magento\TestFramework\Workaround\Override\Fixture\Resolver;

$objectManager = Bootstrap::getObjectManager();
$productFactory = $objectManager->get(ProductInterfaceFactory::class);
$productRepository = $objectManager->get(ProductRepositoryInterface::class);
$productRepository->cleanCache();
$products = [
    [
        'sku' => 'sku-1',
        'name' => 'Simple product',
        'price' => 100000
    ]
];

foreach ($products as $productData) {
    $product = $productFactory->create();
    $product->setTypeId(Type::TYPE_SIMPLE)
        ->setAttributeSetId(4)
        ->setStockData(['qty' => 100, 'is_in_stock' => true, 'manage_stock' => true])
        ->setStatus(Status::STATUS_ENABLED)
        ->setName($productData['name'])
        ->setSku($productData['sku'])
        ->setPrice($productData['price']);
    $productRepository->save($product);
}
```

Luego, en el método que lo requiera, podemos obtener la información de este producto con su repositorio correspondiente:

```php
    public function getProductBySku($sku)
    {
        $productRepository = $objectManager->get(\Magento\Catalog\Api\ProductRepositoryInterface::class);
        return $productRepository->get($sku);
    }
```

También pueden usarse fixtures de otros módulos si es que con eso nos sirve, por ejemplo se puede utilizar el de
Magento_InventoryApi que genera una serie de productos y luego le establece el precio, stock y los asigna a un source:

```php
    /**
    * @magentoDataFixture Magento_InventoryApi::Test/_files/products.php
     */
    public function testSuccessfullyPublishOrder(): void
    {
```

Aunque parezca tedioso todo esto nos sirve para poder establecer una serie de datos con los que podremos contar para
hacer las pruebas correspondientes. Más adelante voy a intentar publicar pruebas más complejas para compartir lo que me
llevó un tiempo entender y que sea más fácil para quién intenta recorrer el camino del buen hábito.  