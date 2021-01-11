# myQow
Evaluates the quality of a website



# Objectif :
## 1. Présence de mentions légales

![](/assets/Capture.PNG)
[.xls download](https://github.com/DavidMolinari/myQow/raw/main/assets/mentions_legales_website.xlsx)
Recherche de "Mentions légales", "Informations légales" dans le code source

## 2.	Date de dernière mise à jour du site web
- Théoriquement tous les serveurs renvoient un header "lastModified" , mais en pratique la réponse de "lastModified" correspond plus ou moins à la date de l'envoie de la requête, ce qui fait que la majorité des site web retournent une réponse de la date actuelle. Peu néanmoins fonctionner avec des site web statiques
- Faire un plugin sur Wayback Machine : https://web.archive.org/web/2020*/https://www.coexel.com/ 

## 3.	Module e-commerce

- Solution payante : Builtwith.com
- Solution faite maison : Recherche des cdn des top 10 plateformes ecommerce
  - BigCommerce
  - Magento.
  - Volusion.
  - Salesforce Commerce Cloud.
  - WooCommerce.
  - 3dcart.
  - Shopify.
  - Kibo.
  - Prestashop.
  - Squarespace.
  - Big Cartel.
  - Wix.
  - Ecwid.
  - Episerver.
  - OpenCart.

## 4.	Possibilité de lire le site en plusieurs langues
- Requête http pour tester un status : 200 => website.com/en/ website.com/fr/

## 5.	Page RH ou recrutement ou carrière,
recherche de keywords : => To Score
"Ressources humaines", "Talent management", "management de talents", "gestion de talents", "Postuler", "recrutement", "RH", "Freelancing", "recruteurs"

## 6.	Temps de chargement d’un site web

```php
// check responsetime for a webbserver
function pingDomain($domain){
    $starttime = microtime(true);
    // supress error messages with @
    $file      = @fsockopen($domain, 80, $errno, $errstr, 10);
    $stoptime  = microtime(true);
    $status    = 0;

    if (!$file){
        $status = -1;  // Site is down
    }
    else{
        fclose($file);
        $status = ($stoptime - $starttime) * 1000;
        $status = floor($status);
    }
    return $status;
}
```
## 7.	Site responsive 


```php
    ini_set('user_agent', 'Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.8.1.9) Gecko/20071025 Firefox/2.0.0.9');
    $html = file_get_contents("http://php.net/");

    ini_set('user_agent', 'Mozilla/5.0 (iPhone; U; CPU iPhone OS 4_0 like Mac OS X; en-us) AppleWebKit/532.9 (KHTML, like Gecko) Version/4.0.5 Mobile/8A293 Safari/6531.22.7');
    $html2 = file_get_contents("http://php.net/");

    similar_text(substr($html,0,1000),substr($html2,0,1000), $similariy);
    echo $similariy."<br>";


if($similariy<50)
        echo "It's responsive";
else
        echo "not responsive";
```


