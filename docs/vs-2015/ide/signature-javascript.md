---
title: '&lt;podpis&gt; (JavaScript) | Dokumentace Microsoftu'
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
- <signature> JavaScript XML tag
- signature JavaScript XML tag
ms.assetid: 319138e7-cfbe-4b37-9643-2ddb7f9c63d4
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0b3278087545a4d49d5f4f2f0d3f6942c4ec6d9a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49293004"
---
# <a name="ltsignaturegt-javascript"></a>&lt;podpis&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Seskupit sadu souvisejících elementů pro funkci nebo metodu jako dokumentace pro přetížené funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<signature externalid="id" externalFile="filename"  
    helpKeyword="keyword" locid="descriptionID">  
</signature>   
```  
  
#### <a name="parameters"></a>Parametry  
 `externalid`  
 Volitelné. Pokud `format` atribut pro [ \<umístění >](../ide/loc-javascript.md) element je `vsdoc`, tento atribut určuje člen ID používaná k nalezení kód XML, který je spojen s podpisem. Na rozdíl od `locid` atribut, tento atribut určuje, že všechny prvky v člena, který se má toto ID se mají načíst. Všechny popisy informace k dispozici v kódu XML se sloučí také s prvky určené v podpisu. To vám umožňuje určit další prvky, jako například `<capability>`, v souboru sajdkára bez zadání ve zdrojovém souboru. `externalid` je volitelný atribut.  
  
 `externalFile`  
 Volitelné. Určuje název souboru, do kterého chcete vyhledat `externalid`. Tento atribut se ignoruje, pokud žádné `externalid` je k dispozici. Toto je volitelný atribut. Výchozí hodnota je název aktuální soubor, ale s příponou .xml místo js. Ve výchozím nastavení pravidla vyhledávání spravovaných prostředků pro lokalizaci slouží k vyhledání souboru.  
  
 `helpKeyword`  
 Volitelné. Klíčové slovo nápovědy klávesy F1.  
  
 `locid`  
 Volitelné. Identifikátor lokalizace informace o poli. Identifikátor je buď členem, nebo ID odpovídá `name` hodnotu v sadě zprávy určené OpenAjax metadat atributu. Typ identifikátoru závisí na formátu určeného v [ \<umístění >](../ide/loc-javascript.md) značky.  
  
## <a name="remarks"></a>Poznámky  
 Použijte jednu `<signature>` – element pro každé přetížené funkce Popis v soubor .js, nebo použijte jednu `<signature>` – element pro každé zadané ID externího člena.  
  
 `<signature>` Elementu musí být umístěn v těle funkce před vykonáním jakýchkoli příkazů. Při použití [ \<summary >](../ide/summary-javascript.md), [ \<param >](../ide/param-javascript.md), nebo [ \<vrátí >](../ide/returns-javascript.md) prvky s `<signature>` elementu umístit další prvky uvnitř `<signature>` bloku.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak používat `<signature>` elementu.  
  
```javascript  
// Use of <signature> with externalid.  
// Requires use of the <loc> tag to identify the external functions.  
function illuminate(light) {  
    /// <signature externalid='M:Windows.Devices.Light.Illuminate()' />  
    /// <signature externalid='M:Windows.Devices.Light.Illuminate(System.Int32)'>  
    ///   <param name='light' type='Number' />  
    /// </signature>  
}  
  
// Use of <signature> for overloads implemented in JavaScript.  
function add(a, b) {  
    /// <signature>  
    /// <summary>function summary 1</summary>  
    /// <param name="a" type="Number">The first number</param>  
    /// <param name="b" type="Number">The second number</param>  
    /// <returns type="Number" />  
    /// </signature>  
    /// <signature>  
    /// <summary>function summary 2 – differ by number of params</summary>  
    /// <param name="a" type="Number">Only 1 parameter</param>  
    /// <returns type="Number" />  
    /// </signature>  
    /// <signature>  
    /// <summary>function summary 3 – differ by parameter type</summary>  
    /// <param name="a" type="Number">Number parameter</param>  
    /// <param name="b" type="String">String parameter</param>  
    /// <returns type="Number" />  
    /// </signature>  
    /// <signature>  
    /// <summary>function summary 4 – differ by return type</summary>  
    /// <param name="a" type="Number">The first number</param>  
    /// <param name="b" type="Number">The second number</param>  
    /// <returns type="String" />  
    /// </signature>  
  
    return a + b;  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Dokumentační komentáře XML](../ide/xml-documentation-comments-javascript.md)



