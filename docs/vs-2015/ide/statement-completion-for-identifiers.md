---
title: Doplňování výrazů pro identifikátory | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IntelliSense [JavaScript], statement completion
- statement completion, JavaScript IntelliSense
ms.assetid: c2cd4945-c67e-471b-8057-96cfd25f7fb2
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d58c5ecc1d787195f7f5c91a07da7a4e775fc27e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49827051"
---
# <a name="statement-completion-for-identifiers"></a>Doplňování výrazů pro identifikátory
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

JavaScript neumožňuje explicitní zadání pro deklarace proměnných. V důsledku toho IntelliSense nemůže vždy poskytnout seznamy dokončení pro objekty. Tato situace může nastat v různých situacích. Následuje několik ty běžné.  
  
- Parametr je deklarovaný, ale to se nevolala jinde v aktivním dokumentu, jak je znázorněno v následujícím příkladu.  
  
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
  
- Objekt je ve funkci, která je volána v reakci na událost. V době návrhu modul IntelliSense nemůže určit typ objektu, který používá v této situaci.  
  
   Pokud modul IntelliSense můžete určit, že události by měla být volána, obvykle prostřednictvím použití `addEventListener` události v aktivním dokumentu přesnější informace technologie IntelliSense neposkytujeme.  
  
  Pokud technologie IntelliSense nedokáže určit objekt, modul IntelliSense naplní seznam pro doplňování s pojmenované entity nebo identifikátory, které jsou k dispozici v aktivním dokumentu. Pokud seznam pro doplňování obsahuje tyto identifikátory, zobrazí se ikony informace vedle sebe. Kromě toho popisek pro každý identifikátor označuje, že výraz neznámý. Následující obrázek znázorňuje příkaz dokončení možnosti pro objekt typu `light` , který nelze identifikovat, protože objekt a jeho vlastnosti, které nejsou definovány. Ale `intensity` vlastnost je k dispozici v seznamu identifikátor, protože se použil v `illuminate` funkce.  
  
  **Možnosti dokončování pro objekt, který nelze identifikovat**  
  
  ![Technologie IntelliSense jazyka JavaScript pro identifikátory](../ide/media/js-intellisense-identifiers.png "js_intellisense_identifiers")  
  
  Seznam dokončení pro objekt lze přepsat pomocí dokumentační komentáře XML nebo funkce rozšíření technologie IntelliSense jazyka JavaScript. Pomocí těchto funkcí, můžete zadat informace o typu a více popisné informace technologie IntelliSense při jinak nebudou k dispozici. Další informace najdete v tématu [rozšíření technologie IntelliSense jazyka JavaScript](../ide/extending-javascript-intellisense.md) a [vytvořit dokumentační komentáře XML](../ide/create-xml-documentation-comments-for-javascript-intellisense.md).  
  
## <a name="see-also"></a>Viz také  
 [JavaScript IntelliSense](../ide/javascript-intellisense.md)



