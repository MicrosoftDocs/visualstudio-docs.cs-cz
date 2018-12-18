---
title: '&lt;pole&gt; (JavaScript) | Dokumentace Microsoftu'
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
- <field> JavaScript XML tag
- field JavaScript XML tag
ms.assetid: c494bae0-3095-42a3-aa0a-4c415188c65c
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a57f84901f2ac6bc691c50fa6d1e3c8b94db6c50
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49939903"
---
# <a name="ltfieldgt-javascript"></a>&lt;pole&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Určuje informace o dokumentaci, včetně popisu, pole nebo člena, který je definován na objekt.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<field name="fieldName" static="true|false"  
    type="FieldType" integer="true|false"  
    domElement="true|false" mayBeNull="true|false"  
    elementType="ArrayElementType" elementInteger="true|false"  
    elementDomElement="true|false" elementMayBeNull="true|false"  
    helpKeyword="keyword" locid="descriptionID"  
    value="code">description  
</field>  
```  
  
#### <a name="parameters"></a>Parametry  
 `name`  
 Název pole nebo člen. Když `<field>` element se používá v funkce konstruktoru, `name` je povinná a definuje člen, ke kterému se vztahuje na značku. Když `<field>` element je přímo zadávání poznámek do pole, tento atribut se ignoruje a název používaný aplikací Visual Studio je název skutečné pole ve zdrojovém kódu.  
  
 `static`  
 Volitelné. Určuje, zda je pole členem funkce konstruktoru nebo členem objektu vrácené funkcí konstruktoru. Nastavte na `true` považovat za pole členské funkce konstruktoru. Nastavte na `false` pole považovat za členem objektu vrácené funkcí konstruktoru.  
  
 `type`  
 Volitelné. Datový typ pole. Typ může být jeden z následujících akcí:  
  
- Zadejte jazyka ECMAScript specifikací ECMAScript 5, třeba `Number` a `Object`.  
  
- Modelu DOM, jako objekt `HTMLElement`, `Window`, a `Document`.  
  
- Funkce jazyka JavaScript konstruktoru.  
  
  `integer`  
  Volitelné. Pokud `type` je `Number`, určuje, zda je pole celé číslo. Nastavte na `true` k označení, že pole je celé číslo; v opačném případě nastavte na `false`. Tento atribut není používá sada Visual Studio k poskytování informací technologie IntelliSense.  
  
  `domElement`  
  Volitelné. Tento atribut je zastaralá; `type` atribut má přednost před tento atribut. Tento atribut určuje, zda je pole zdokumentovaných prvek modelu DOM. Nastavte na `true` k určení, že pole je prvek modelu DOM; v opačném případě nastavte na `false`. Pokud `type` není nastaven atribut a `domElement` je nastavena na `true`, technologie IntelliSense jsou považovány za zdokumentovaných pole `HTMLElement` při dokončování příkazů.  
  
  `mayBeNull`  
  Volitelné. Určuje, jestli dokument pole lze nastavit na hodnotu null. Nastavte na `true` k označení, že pole může být nastaven na hodnotu null; jinak vrátí hodnotu, nastavte na `false`. Výchozí hodnota je `false`. Tento atribut není používá sada Visual Studio k poskytování informací technologie IntelliSense.  
  
  `elementType`  
  Volitelné. Pokud `type` je `Array`, tento atribut určuje typ prvků v poli.  
  
  `elementInteger`  
  Volitelné. Pokud `type` je `Array` a `elementType` je `Number`, tento atribut určuje, zda jsou prvky v poli celých čísel. Nastavte na `true` k označení, který prvků v poli jsou celá čísla; v opačném případě nastavte na `false`. Tento atribut není používá sada Visual Studio k poskytování informací technologie IntelliSense.  
  
  `elementDomElement`  
  Volitelné. Tento atribut je zastaralá; `elementType` atribut má přednost před tento atribut. Pokud `type` je `Array`, tento atribut určuje, zda prvků v poli jsou prvky modelu DOM. Nastavte na `true` k určení, které prvky jsou prvky modelu DOM; v opačném případě nastavte na `false`. Pokud `elementType` není nastaven atribut a `elementDomElement` je nastavena na `true`, technologie IntelliSense zpracovává každý prvek v poli jako `HTMLElement` při dokončování příkazů.  
  
  `elementMayBeNull`  
  Volitelné. Pokud `type` je `Array`, určuje, zda prvků v poli může být nastavena na hodnotu null. Nastavte na `true` k označení, že prvků v poli může být nastaven na hodnotu null; jinak vrátí hodnotu, nastavte na `false`. Výchozí hodnota je `false`. Tento atribut není používá sada Visual Studio k poskytování informací technologie IntelliSense.  
  
  `helpKeyword`  
  Volitelné. Klíčové slovo nápovědy klávesy F1.  
  
  `locid`  
  Volitelné. Identifikátor lokalizace informace o poli. Identifikátor je buď členem, nebo ID odpovídá `name` hodnotu v sadě zprávy určené OpenAjax metadat atributu. Typ identifikátoru závisí na formátu určeného v [ \<umístění >](../ide/loc-javascript.md) značky.  
  
  `value`  
  Volitelné. Určuje kód, který by se mělo vyhodnotit pro použití technologií IntelliSense místo samotný kód funkce. Pro `<field>`, tento atribut je podporován pro funkce konstruktoru, ale není podporovaná pro literály objektů. Pomocí tohoto atributu je poskytnout informace o typu při typ pole není definován. Například můžete použít `value=’1’` považovat typ pole jako číslo.  
  
  `description`  
  Volitelné. Popis pro pole.  
  
## <a name="remarks"></a>Poznámky  
 `name` Atribut je vyžadován, když jste dokumentace pole v funkce konstruktoru. Pro všechny další scénáře, všechny atributy pro `<field>` element jsou volitelné.  
  
 Pokud jste dokumentaci funkce konstruktoru `<field>` elementu musí být bezprostředně před deklaraci pole. `name` Atributu musí odpovídat názvu, který se používá ve zdrojovém kódu. Pro členy objektu `name` atribut lze vynechat, pokud `<field>` prvek se zobrazuje bezprostředně před deklaraci člena objektu.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak používat `<field>` elementu.  
  
```javascript  
// Use of <field> in an object definition.  
var Rectangle = {  
    /// <field type='Number'>The width of the rectangle.</field>  
    wid: 5,  
    /// <field type='Number'>The length of the rectangle.</field>  
    len: 0,  
    /// <field type='Number'>Returns the area of the rectangle.</field>  
    getArea: function (wid, len) {  
        return len * wid;  
    }  
}  
  
// Use of <field> in a constructor function.  
// The name attribute is required.  
function Engine() {  
    /// <field name='HorsePower' type='Number'>The engine's horsepower.</field>  
    this.HorsePower = 150;  
}  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití `<field>` křížkem `static` atribut nastaven na `true`.  
  
```javascript  
function Engine() {  
    /// <field name='HorsePower' static='true' type='Number'>static field desc.</field>  
}  
  
Engine.HorsePower = 140;  
// IntelliSense on the field is available here.  
Engine.  
  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití `<field>` křížkem `static` atribut nastaven na `false`.  
  
```javascript  
function Engine() {  
    /// <field name='HorsePower' static='false' type='Number'>Non-static field desc.</field>  
}  
  
Engine.HorsePower = 140;  
var eng = new Engine();  
// IntelliSense on the field is available here.  
eng.  
  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití `<field>` křížkem `value` atribut.  
  
```javascript  
function calculator(a) {  
    /// <field name='f' value='1'/>  
}  
new calculator().f.   // Completion list for a Number.  
  
```  
  
## <a name="see-also"></a>Viz také  
 [Dokumentační komentáře XML](../ide/xml-documentation-comments-javascript.md)



