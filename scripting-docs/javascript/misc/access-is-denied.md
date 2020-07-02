---
title: Přístup byl odepřen | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 8a512060-d744-47af-a83e-4ba42ea2c5b2
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 874f7c0e5dcfaf4881c059a77f1c5e930d8c0578
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85814834"
---
# <a name="access-is-denied"></a>Přístup byl odepřen.
Skript se pokusil o přístup k datům ze zdroje, který je jiný než hostitel aktuální stránky. Stejné zásady původu, za kterými následuje Internet Explorer a další prohlížeče, umožňují skriptům přístup k datům pouze ze zdrojů se stejným schématem, hostitelem a portem adresy URL aktuální stránky.  
  
 Pokud je aktuální stránka například `https://employees.mycompany.com` , nemůžete získat přístup k datům z následujících adres URL:  
  
- `http://data.contoso.com`, protože používá protokol HTTP místo protokolu HTTPS.  
  
- `https://somedatasource.com`, protože se jedná o jinou doménu.  
  
- `https://employees.mycompany.com:8888`, protože používá jiný port.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Prozkoumejte, jestli rozhraní API, které zkoušíte volat, podporuje JSONP nebo CORS, což jsou dvě metody, které umožňují bezpečné skriptování mezi zdroji.  
  
- Pokud se pokoušíte zavolat REST API, refaktorujte toto volání do kódu na straně serveru a pak vystavte nový koncový bod REST pro skripty na straně klienta.  
  
     Další informace najdete v online dokumentaci týkající se stejných zásad původu, JSONP a CORS.
