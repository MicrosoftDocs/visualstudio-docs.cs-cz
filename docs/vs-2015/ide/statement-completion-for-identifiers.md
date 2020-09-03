---
title: Dokončování příkazů pro identifikátory | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense [JavaScript], statement completion
- statement completion, JavaScript IntelliSense
ms.assetid: c2cd4945-c67e-471b-8057-96cfd25f7fb2
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f5e52bf174e5a41d79fa23bfca39121db668e40e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72643860"
---
# <a name="statement-completion-for-identifiers"></a>Doplňování výrazů pro identifikátory
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

JavaScript nepovoluje explicitní psaní pro deklarace proměnných. V důsledku toho technologie IntelliSense nemůže vždy poskytovat seznamy dokončení pro objekty. K tomu může dojít v různých situacích. Následuje několik běžných.

- Parametr je deklarován, ale nebyl volán jinde v aktivním dokumentu, jak je znázorněno v následujícím příkladu.

  ```javascript
  function illuminate(light) {
           light.  // Accurate statement completion is not available
                   // unless illuminate is called elsewhere with a
                   // parameter that has a value. If it is called only
                   // in a function that is a sibling to
                   // illuminate(light) in the call hierarchy, the
                   // IntelliSense engine also cannot determine the
                   // parameter type.
       }

  // Sibling function. No statement completion for light
  // object in preceding code.
  function lightLamp() {
      var x = illuminate(1);
  }

  // Uncomment the next line to obtain statement completion for
  // light object in preceding code.
  // var x = illuminate(1);
  ```

- Objekt je ve funkci, která je volána jako odpověď na událost. V době návrhu nemůže modul IntelliSense určit typ objektů použitých v této situaci.

   Pokud modul IntelliSense může určit, že by měla být událost volána, obvykle prostřednictvím použití `addEventListener` pro událost v aktivním dokumentu, jsou k dispozici přesnější informace technologie IntelliSense.

  Když technologie IntelliSense nemůže identifikovat objekt, vyplní modul IntelliSense seznam dokončení pomocí pojmenovaných entit nebo identifikátorů, které jsou k dispozici v aktivním dokumentu. Když seznam pro dokončení obsahuje tyto identifikátory, zobrazí se vedle něj informační ikony. Kromě toho popis výrazu pro každý identifikátor označuje, že výraz není znám. Následující ilustrace znázorňuje možnosti dokončování příkazů pro objekt typu `light` , který nelze identifikovat, protože objekt a jeho vlastnosti jsou nedefinovány. Tato `intensity` vlastnost je však k dispozici v seznamu identifikátorů, protože byla použita ve `illuminate` funkci.

  **Možnosti dokončení objektu, který nelze identifikovat**

  ![JavaScriptová technologie IntelliSense pro identifikátory](../ide/media/js-intellisense-identifiers.png "js_intellisense_identifiers")

  Můžete přepsat seznam dokončení pro objekt pomocí dokumentačních komentářů XML nebo funkcí rozšíření JavaScript IntelliSense. Pomocí těchto funkcí můžete poskytnout informace o typu a výstižnější informace technologie IntelliSense, pokud nemusí být jinak k dispozici. Další informace najdete v tématu [rozšíření JavaScriptu IntelliSense](../ide/extending-javascript-intellisense.md) a [vytváření dokumentačních komentářů XML](../ide/create-xml-documentation-comments-for-javascript-intellisense.md).

## <a name="see-also"></a>Viz také
 [JavaScript IntelliSense](../ide/javascript-intellisense.md)
