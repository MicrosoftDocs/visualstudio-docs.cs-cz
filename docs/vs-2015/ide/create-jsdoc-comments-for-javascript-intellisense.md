---
title: Vytváření komentářů JSDoc pro JavaScript IntelliSense | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: a0dadc81-3755-4a47-bcee-c1010819ff2a
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b974f3450b88ab22e58e284881f270c1b3d72298
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72619278"
---
# <a name="create-jsdoc-comments-for-javascript-intellisense"></a>Vytvoření komentářů JSDoc pro JavaScript IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Technologie IntelliSense v aplikaci Visual Studio zobrazuje informace, které přidáte do skriptu pomocí standardních komentářů JSDoc. Komentáře JSDoc lze použít k poskytnutí informací o prvcích kódu, jako jsou například funkce, pole a proměnné.

## <a name="jsdoc-comment-tags"></a>Značky komentářů JSDoc
 Následující značky standardních komentářů JSDoc jsou používány technologií IntelliSense k zobrazení informací o kódu.

|  Značka JSDoc   |                       Syntaxe                        |                                                     Poznámky                                                      |
|--------------|-----------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
| @deprecated  |              *popis* @deprecated              |                                   Určuje vystaralou funkci nebo metodu.                                   |
| @description |             *popis* @description              |                              Určuje popis funkce nebo metody.                               |
|    @param    | <em>popis</em> @param {*Type*} *ParameterName* | Určuje informace pro parametr v rámci funkce nebo metody.<br /><br /> TypeScript podporuje taky @paramTag. |
|  @property   |          @property {*Type*} *PropertyName*          |   Určuje informace, včetně popisu, pro pole nebo člena, který je definován v objektu.    |
|   @returns   |                  @returns {*Type*}                  |           Určuje návratovou hodnotu.<br /><br /> Pro TypeScript použijte @returnType místo @returns.           |
|   @summary   |               *popis* @summary                |                   Určuje popis funkce nebo metody (stejné jako @description).                   |
|    @type     |                   @type {*Type*}                    |                                Určuje typ konstanty nebo proměnné.                                |
|   @typedef   |         @typedef {*Type*} *customTypeName*          |                                            Určuje vlastní typ.                                            |

### <a name="examples"></a>Příklady
 Následující příklad ukazuje použití značek @description, @param a @return JSDoc pro funkci s názvem `getArea`.

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

 V předchozím příkladu IntelliSense zobrazí popis, parametr a návratové informace, když zadáte levou závorku pro `getArea`.

 ![Informace o IntelliSense pro funkci](../ide/media/js-intellisense-jsdoc-comments.png "JS_IntelliSense_JSDoc_Comments")

 Následující příklad ukazuje, jak použít značku @typedef se značkou @property.

```javascript
/**
  * @typedef {object} Weather
  * @property {string} current The current weather.
  */
function getForecast(Weather) {
}

var w = new Weather();
```

 Následující příklad ukazuje použití značek @type JSDoc. Jak je znázorněno v tomto příkladu, nejsou vyžadovány jednoduché hvězdičky (*), které následují po počáteční dvojici hvězdičky (\* \*).

```javascript
/**
    @type {string}
*/
const RED = 'FF0000';

```

 Následující příklad ukazuje, jak použít značku JSDoc @deprecated.

```javascript
/**
 * @deprecated since version 2.0
 */
function old() {
}
```
