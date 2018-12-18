---
title: Vytvoření komentářů JSDoc pro JavaScript IntelliSense | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a0dadc81-3755-4a47-bcee-c1010819ff2a
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9d338b2bece99f720670871a1b92c6b2a57c4280
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49908584"
---
# <a name="create-jsdoc-comments-for-javascript-intellisense"></a>Vytvoření komentářů JSDoc pro JavaScript IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Technologie IntelliSense v sadě Visual Studio zobrazí informace, které přidáte do skriptu s využitím standardních komentářů JSDoc. Komentáře JSDoc můžete použít k poskytnutí informací o kódu prvky, jako jsou functions, polí a proměnné.  

## <a name="jsdoc-comment-tags"></a>Značky pro komentáře JSDoc  
 Následující standardních značek komentářů JSDoc se používají technologii IntelliSense pro zobrazení informací o kódu.  


|  Značka JSDoc   |                       Syntaxe                        |                                                     Poznámky                                                      |
|--------------|-----------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
| @deprecated  |              @deprecated *Popis*              |                                   Určuje zastaralé funkce nebo metody.                                   |
| @description |             @description *Popis*              |                              Určuje popis pro funkci nebo metodu.                               |
|    @param    | @param {*typ*} *parameterName*<em>popis</em> | Určuje informace o parametru ve funkci nebo metodu.<br /><br /> TypeScript podporuje také @paramTag. |
|  @property   |          @property {*typ*} *propertyName*          |   Určuje informace, včetně popisu, pole nebo člena, který je definován na objekt.    |
|   @returns   |                  @returns {*typ*}                  |           Určuje návratovou hodnotu.<br /><br /> TypeScript, použijte @returnType místo @returns.           |
|   @summary   |               @summary *Popis*                |                   Určuje popis pro funkci nebo metodu (stejné jako @description).                   |
|    @type     |                   @type {*typ*}                    |                                Určuje typ konstanty nebo proměnné.                                |
|   @typedef   |         @typedef {*typ*} *customTypeName*          |                                            Určuje vlastního typu.                                            |

### <a name="examples"></a>Příklady  
 Následující příklad ukazuje použití @description, @param, a @return JSDoc značky pro funkci s názvem `getArea`.  

```javascript  
/** @description Determines the area of a circle that has the specified radius parameter.  
 * @param {number} radius The radius of the circle.  
 * @return {number}  
 */  
function getArea(radius) {  
    var areaVal;  
    areaVal = Math.PI * radius * radius;  
    return areaVal;  
}  
```  

 V předchozím příkladu, technologie IntelliSense zobrazuje popis, parametru a vrácené informace při psaní levou závorku pro `getArea`.  

 ![Informace IntelliSense pro funkci](../ide/media/js-intellisense-jsdoc-comments.png "JS_IntelliSense_JSDoc_Comments")  

 Následující příklad ukazuje způsob použití @typedef označit @property značky.  

```javascript  
/**  
  * @typedef {object} Weather  
  * @property {string} current The current weather.  
  */  
function getForecast(Weather) {  
}  

var w = new Weather();  
```  

 Následující příklad ukazuje použití @type JSDoc značky. Jak je znázorněno v tomto příkladu, jeden hvězdičky (*), které následují pár počáteční hvězdičkou (\*\*) se nevyžadují.  

```javascript  
/**  
    @type {string}  
*/  
const RED = 'FF0000';  

```  

 Následující příklad ukazuje způsob použití @deprecated značka JSDoc.  

```javascript  
/**  
 * @deprecated since version 2.0  
 */  
function old() {  
}  
```



