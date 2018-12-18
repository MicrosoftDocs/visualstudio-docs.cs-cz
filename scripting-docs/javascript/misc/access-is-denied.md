---
title: Přístup byl odepřen. | Dokumentace Microsoftu
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 8a512060-d744-47af-a83e-4ba42ea2c5b2
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 9b49f60395a853d7dfda91738ccccaba9d585b46
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295160"
---
# <a name="access-is-denied"></a>Přístup byl odepřen.
Skript se pokusila o přístup k datům ze zdroje než hostitele aktuální stránky. Zásada stejného původu, za nímž následuje aplikace Internet Explorer a ostatní prohlížeče umožňuje skripty pro přístup k datům jenom ze zdroje se stejné schéma, hostitele a portu z adresy URL aktuální stránky.  
  
 Například, pokud je aktuální stránku `https://employees.mycompany.com`, nelze přístup k datům z následující adresy URL:  
  
-   `http://data.contoso.com`, protože používá protokol HTTP místo protokolu HTTPS.  
  
-   `https://somedatasource.com`, protože je jinou doménu.  
  
-   `https://employees.mycompany.com:8888`, protože ho používá jiný port.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Zjistěte, jestli podporuje rozhraní API, které se snažíte volat JSONP nebo CORS, která se používají dva přístupy, které bezpečně povolit skriptování nepůvodního zdroje.  
  
-   Pokud se snažíte volat rozhraní REST API, Refaktorovat toto volání do kódu na straně serveru, pak vystavit nový koncový bod REST pro skripty na straně klienta.  
  
     Další informace najdete online dokumentaci týkající se zásada stejného zdroje, JSONP a CORS.
