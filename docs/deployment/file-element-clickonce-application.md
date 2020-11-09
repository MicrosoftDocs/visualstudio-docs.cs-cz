---
title: '&lt;File – &gt; element (aplikace ClickOnce) | Microsoft Docs'
description: Element File identifikuje všechny neassembly soubory stažené a používané aplikací. Element File je nepovinný.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://www.w3.org/2000/09/xmldsig#Transform
- urn:schemas-microsoft-com:asm.v2#file
- http://www.w3.org/2000/09/xmldsig#DigestValue
- http://www.w3.org/2000/09/xmldsig#DigestMethod
- http://www.w3.org/2000/09/xmldsig#Transforms
- urn:schemas-microsoft-com:asm.v2#hash
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <file> element [ClickOnce application manifest]
- manifests [ClickOnce], file element
ms.assetid: 56e3490c-eed5-4841-b1bf-eefe778b6ac9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9a4d09d4a0e141359b066f2af31c158f36c96522
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2020
ms.locfileid: "94382738"
---
# <a name="ltfilegt-element-clickonce-application"></a>&lt;File – &gt; element (aplikace ClickOnce)
Identifikuje všechny neassembly soubory stažené a používané aplikací.

## <a name="syntax"></a>Syntax

```xml
<file
    name
    size
    group
    optional
    writeableType
>
    <typelib
        tlbid
        version
        helpdir
        resourceid
        flags
    />
    <comClass
        clsid
        description
        threadingModel
        tlbid
        progid
        miscStatus
        miscStatusIcon
        miscStatusContent
        miscStatusDocPrint
        miscStatusThumbnail
    />
    <comInterfaceExternalProxyStub
        iid
        baseInterface
        numMethods
        name
        tlbid
        proxyStubClass32
    />
    <comInterfaceProxyStub
        iid
        baseInterface
        numMethods
        name
        tlbid
        proxyStubClass32
    />
    <windowClass
        versioned
    />
</file>
```

## <a name="elements-and-attributes"></a>Elementy a atributy
 `file`Element je nepovinný. Element má následující atributy.

|Atribut|Popis|
|---------------|-----------------|
|`name`|Povinná hodnota. Určuje název souboru.|
|`size`|Povinná hodnota. Určuje velikost souboru v bajtech.|
|`group`|Volitelné, pokud `optional` atribut není zadán nebo je nastaven na hodnotu `false` ; požadováno v případě, že `optional` je `true` . Název skupiny, do které tento soubor patří. Název může být libovolná hodnota řetězce Unicode zvolená vývojářem, která se používá ke stahování souborů na vyžádání s <xref:System.Deployment.Application.ApplicationDeployment> třídou.|
|`optional`|Nepovinný parametr. Určuje, jestli se tento soubor musí stáhnout při prvním spuštění aplikace, nebo jestli se má soubor umístit na server, dokud ho aplikace na vyžádání nepožaduje. Pokud `false` je tento soubor nebo nedefinovaný, stáhne se při prvním spuštění nebo instalaci aplikace. Pokud je `true` `group` nutné zadat pro manifest aplikace platnou hodnotu. `optional` Pokud `writeableType` je zadaný s hodnotou, nemůže mít hodnotu true `applicationData` .|
|`writeableType`|Nepovinný parametr. Určuje, že tento soubor je datovým souborem. V současné době je jediná platná hodnota `applicationData` .|

## <a name="typelib"></a>Export
 `typelib`Element je volitelný podřízený prvek souboru. Element popisuje knihovnu typů, která patří do komponenty modelu COM. Element má následující atributy.

|Atribut|Popis|
|---------------|-----------------|
|`tlbid`|Povinná hodnota. Identifikátor GUID přiřazený k knihovně typů|
|`version`|Povinná hodnota. Číslo verze knihovny typů.|
|`helpdir`|Povinná hodnota. Adresář, který obsahuje soubory s nápovědu pro komponentu. Může mít nulovou délku.|
|`resourceid`|Nepovinný parametr. Šestnáctková řetězcová reprezentace identifikátoru národního prostředí (LCID). Jedná se o jedno až čtyři šestnáctkové číslice bez předpony 0x a bez počátečních nul. Identifikátor LCID může mít neutrální identifikátor subjazyka.|
|`flags`|Nepovinný parametr. Řetězcové vyjádření příznaků knihovny typů pro tuto knihovnu typů. Konkrétně by měl být jeden z "omezený", "CONTROL", "HIDDEN" a "HASDISKIMAGE".|

## <a name="comclass"></a>comClass
 `comClass`Element je volitelný podřízený `file` prvek, ale je vyžadován, pokud [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace obsahuje komponentu modelu COM, kterou zamýšlí nasadit pomocí modelu COM bez registrace. Element má následující atributy.

|Atribut|Popis|
|---------------|-----------------|
|`clsid`|Povinná hodnota. ID třídy komponenty modelu COM vyjádřené jako identifikátor GUID.|
|`description`|Nepovinný parametr. Název třídy.|
|`threadingModel`|Nepovinný parametr. Model vláken používaný v rámci vnitroprocesové třídy COM. Pokud má tato vlastnost hodnotu null, není použit žádný model vláken. Komponenta je vytvořena v hlavním vlákně klienta a volání z jiných vláken jsou zařazena do tohoto vlákna. V následujícím seznamu jsou uvedeny platné hodnoty:<br /><br /> `Apartment`, `Free` , `Both` a `Neutral` .|
|`tlbid`|Nepovinný parametr. Identifikátor GUID pro knihovnu typů pro tuto komponentu COM|
|`progid`|Nepovinný parametr. Programový identifikátor závislý na verzi spojený s komponentou modelu COM. Formát `ProgID` je `<vendor>.<component>.<version>` .|
|`miscStatus`|Nepovinný parametr. V manifestu sestavení jsou duplicity informace poskytované `MiscStatus` klíčem registru. Pokud `miscStatusIcon` `miscStatusContent` `miscStatusDocprint` `miscStatusThumbnail` se nenaleznou hodnoty atributů,, nebo, `miscStatus` použije se pro chybějící atributy odpovídající výchozí hodnota uvedená v části. Hodnota může být čárkami oddělený seznam hodnot atributů z následující tabulky. Tento atribut můžete použít, pokud je třída modelu COM Třída OCX, která vyžaduje `MiscStatus` hodnoty klíče registru.|
|`miscStatusIcon`|Nepovinný parametr. V manifestu sestavení jsou duplicity informace, které poskytuje DVASPECT_ICON. Může poskytnout ikonu objektu. Hodnota může být čárkami oddělený seznam hodnot atributů z následující tabulky. Tento atribut můžete použít, pokud je třída modelu COM Třída OCX, která vyžaduje `Miscstatus` hodnoty klíče registru.|
|`miscStatusContent`|Nepovinný parametr. V manifestu sestavení jsou duplicity informace, které poskytuje DVASPECT_CONTENT. Může poskytovat pro obrazovku nebo tiskárnu složený dokument. Hodnota může být čárkami oddělený seznam hodnot atributů z následující tabulky. Tento atribut můžete použít, pokud je třída modelu COM Třída OCX, která vyžaduje `MiscStatus` hodnoty klíče registru.|
|`miscStatusDocPrint`|Nepovinný parametr. V manifestu sestavení jsou duplicity informace, které poskytuje DVASPECT_DOCPRINT. Může poskytnout reprezentace objektu na obrazovce, jako kdyby byla vytištěna na tiskárně. Hodnota může být čárkami oddělený seznam hodnot atributů z následující tabulky. Tento atribut můžete použít, pokud je třída modelu COM Třída OCX, která vyžaduje `MiscStatus` hodnoty klíče registru.|
|`miscStatusThumbnail`|Nepovinný parametr. Duplikáty v sestavení manifestují informace, které poskytuje DVASPECT_THUMBNAIL. Může poskytnout miniaturu objektu zobrazitelného v nástroji pro procházení. Hodnota může být čárkami oddělený seznam hodnot atributů z následující tabulky. Tento atribut můžete použít, pokud je třída modelu COM Třída OCX, která vyžaduje `MiscStatus` hodnoty klíče registru.|

## <a name="cominterfaceexternalproxystub"></a>comInterfaceExternalProxyStub
 `comInterfaceExternalProxyStub`Element je volitelný podřízený `file` prvek elementu, ale může být vyžadován, pokud [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace obsahuje komponentu com, kterou zamýšlí nasadit pomocí modelu COM bez registrace. Element obsahuje následující atributy.

|Atribut|Popis|
|---------------|-----------------|
|`iid`|Povinná hodnota. IDENTIFIKÁTOR rozhraní (IID), který je obsluhován tímto proxy serverem. Identifikátor IID musí mít kolem sebe závorky.|
|`baseInterface`|Nepovinný parametr. IID rozhraní, ze kterého je odvozeno rozhraní, na které odkazuje `iid` .|
|`numMethods`|Nepovinný parametr. Počet metod implementovaných rozhraním.|
|`name`|Nepovinný parametr. Název rozhraní, jak se bude zobrazovat v kódu.|
|`tlbid`|Nepovinný parametr. Knihovna typů, která obsahuje popis rozhraní určeného `iid` atributem.|
|`proxyStubClass32`|Nepovinný parametr. Mapuje IID na identifikátor CLSID v 32 proxy DLL.|

## <a name="cominterfaceproxystub"></a>comInterfaceProxyStub
 `comInterfaceProxyStub`Element je volitelný podřízený `file` prvek elementu, ale může být vyžadován, pokud [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace obsahuje komponentu com, kterou zamýšlí nasadit pomocí modelu COM bez registrace. Element obsahuje následující atributy.

|Atribut|Popis|
|---------------|-----------------|
|`iid`|Povinná hodnota. IDENTIFIKÁTOR rozhraní (IID), který je obsluhován tímto proxy serverem. Identifikátor IID musí mít kolem sebe závorky.|
|`baseInterface`|Nepovinný parametr. IID rozhraní, ze kterého je odvozeno rozhraní, na které odkazuje `iid` .|
|`numMethods`|Nepovinný parametr. Počet metod implementovaných rozhraním.|
|`Name`|Nepovinný parametr. Název rozhraní, jak se bude zobrazovat v kódu.|
|`Tlbid`|Nepovinný parametr. Knihovna typů, která obsahuje popis rozhraní určeného `iid` atributem.|
|`proxyStubClass32`|Nepovinný parametr. Mapuje IID na identifikátor CLSID v 32 proxy DLL.|
|`threadingModel`|Nepovinný parametr. Nepovinný parametr. Model vláken používaný v rámci vnitroprocesové třídy COM. Pokud má tato vlastnost hodnotu null, není použit žádný model vláken. Komponenta je vytvořena v hlavním vlákně klienta a volání z jiných vláken jsou zařazena do tohoto vlákna. V následujícím seznamu jsou uvedeny platné hodnoty:<br /><br /> `Apartment`, `Free` , `Both` a `Neutral` .|

## <a name="windowclass"></a>windowClass
 `windowClass`Element je volitelný podřízený `file` prvek elementu, ale může být vyžadován, pokud [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace obsahuje komponentu com, kterou zamýšlí nasadit pomocí modelu COM bez registrace. Element odkazuje na třídu okna definovanou komponentou modelu COM, u které musí být použita verze. Element obsahuje následující atributy.

|Atribut|Popis|
|---------------|-----------------|
|`versioned`|Nepovinný parametr. Určuje, zda název třídy vnitřního okna používaného v registraci obsahuje verzi sestavení, která obsahuje třídu okna. Hodnota tohoto atributu může být `yes` nebo `no` . Výchozí formát je `yes`. Hodnota `no` by měla být použita pouze v případě, že je stejná třída okna definována souběžnou komponentou a ekvivalentní nesouběžná komponenta a chcete ji považovat za stejnou třídu okna. Všimněte si, že jsou k dispozici obvyklá pravidla o registraci třídy okna – pouze první komponenta, která registruje třídu okna, ji bude moci zaregistrovat, protože pro ni není použita verze.|

## <a name="hash"></a>hash
 `hash`Element je volitelný podřízený `file` prvek elementu. `hash`Element nemá žádné atributy.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] používá algoritmus hash pro všechny soubory v aplikaci jako kontrolu zabezpečení, aby se zajistilo, že žádný ze souborů nebyl po nasazení změněn. Není `hash` -li prvek zahrnut, tato kontrolu nebude provedena. Proto vynechání `hash` elementu není doporučeno.

 Pokud manifest obsahuje soubor, který nemá hodnotu hash, nemůže být tento manifest digitálně podepsán, protože uživatelé nemohou ověřit obsah nezatřiďovacího souboru.

## <a name="dsigtransforms"></a>dsig: transformes
 `dsig:Transforms`Element je požadovaný podřízený `hash` prvek elementu. `dsig:Transforms`Element nemá žádné atributy.

## <a name="dsigtransform"></a>dsig: transformace
 `dsig:Transform`Element je požadovaný podřízený `dsig:Transforms` prvek elementu. `dsig:Transform`Element má následující atributy.

| Atribut | Popis |
|-------------| - |
| `Algorithm` | Algoritmus použitý k výpočtu hodnoty Digest pro tento soubor. Aktuálně jediná hodnota, kterou používá, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] je `urn:schemas-microsoft-com:HashTransforms.Identity` . |

## <a name="dsigdigestmethod"></a>dsig:DigestMethod
 `dsig:DigestMethod`Element je požadovaný podřízený `hash` prvek elementu. `dsig:DigestMethod`Element má následující atributy.

| Atribut | Popis |
|-------------| - |
| `Algorithm` | Algoritmus použitý k výpočtu hodnoty Digest pro tento soubor. Aktuálně jediná hodnota, kterou používá, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] je `http://www.w3.org/2000/09/xmldsig#sha1` . |

## <a name="dsigdigestvalue"></a>dsig: DigestValue
 `dsig:DigestValue`Element je požadovaný podřízený `hash` prvek elementu. `dsig:DigestValue`Element nemá žádné atributy. Jeho textová hodnota je vypočtená hodnota hash pro zadaný soubor.

## <a name="remarks"></a>Poznámky
 Tento prvek identifikuje všechny nesestavení soubory, které tvoří aplikaci, a zejména hodnoty hash pro ověření souboru. Tento element může také zahrnovat data izolace modelu COM (Component Object Model) přidružená k souboru. Pokud se soubor změní, je nutné aktualizovat soubor manifestu aplikace také, aby odrážel změnu.

## <a name="example"></a>Příklad
 Následující příklad kódu ukazuje `file` prvky v manifestu aplikace pro aplikaci nasazenou pomocí [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

```xml
<file name="Icon.ico" size="9216">
  <hash>
    <dsig:Transforms>
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />
    </dsig:Transforms>
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
    <dsig:DigestValue>lVoj+Rh6RQ/HPNLOdayQah5McrI=</dsig:DigestValue>
  </hash>
</file>
```

## <a name="see-also"></a>Viz také
- [Manifest aplikace ClickOnce](../deployment/clickonce-application-manifest.md)