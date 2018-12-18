---
title: '&lt;soubor&gt; – Element (aplikace ClickOnce) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 16c301d55738519f3e097138f08b6b2c2fe2b4c7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49270735"
---
# <a name="ltfilegt-element-clickonce-application"></a>&lt;soubor&gt; – Element (aplikace ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identifikuje všechny soubory nonassembly stáhli a použili aplikací.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 `file` Element je volitelné. Element má následující atributy.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`name`|Požadováno. Určuje název souboru.|  
|`size`|Požadováno. Určuje velikost v bajtech souboru.|  
|`group`|Volitelné, pokud `optional` atribut není zadán, nebo nastavte `false`; požadováno pokud `optional` je `true`. Název skupiny, do které tento soubor patří. Název může být libovolná hodnota řetězce Unicode zvolený vývojářem a slouží pro stahování souborů na vyžádání s využitím <xref:System.Deployment.Application.ApplicationDeployment> třídy.|  
|`optional`|Volitelné. Určuje, zda musí tento soubor ke stažení aplikace při prvním spuštění nebo zda soubor by měl být uložen pouze na serveru dokud aplikace nevyžaduje na vyžádání. Pokud `false` nebo nedefinovaný, soubor se stáhne, při prvním spuštění nebo nainstalované aplikace. Pokud `true`, `group` platný manifest aplikace se musí zadat. `optional` nemůže být true, pokud `writeableType` určena s hodnotou `applicationData`.|  
|`writeableType`|Volitelné. Určuje, že tento soubor je soubor datovým souborem. Momentálně je jediná platná hodnota `applicationData`.|  
  
## <a name="typelib"></a>knihovny typů  
 `typelib` Element je volitelný podřízený prvek souboru. Element popisuje knihovnu typů, který patří do komponenty modelu COM. Element má následující atributy.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`tlbid`|Požadováno. Identifikátor GUID přiřazený do knihovny typů.|  
|`version`|Požadováno. Číslo verze knihovny typů.|  
|`helpdir`|Požadováno. Adresář, který obsahuje soubory nápovědy pro komponentu. Může být nulové délky.|  
|`resourceid`|Volitelné. Šestnáctkový řetězec reprezentuje identifikátor národního prostředí (LCID). Je jednou až čtyřmi šestnáctkovými číslicemi bez předpony 0 x a bez počátečních nul. Identifikátor LCID může mít identifikátor dílčího neutrální.|  
|`flags`|Volitelné. Řetězcová reprezentace příznaků knihovny typů pro tuto knihovnu typů. Konkrétně je třeba použít jeden "OMEZENO", "CONTROL", "HIDDEN" a "HASDISKIMAGE".|  
  
## <a name="comclass"></a>comClass  
 `comClass` Je volitelný podřízený element `file` elementu, ale je vyžadováno, pokud [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace obsahuje komponentu modelu COM, který chce nasadit pomocí modelu COM bez registrace Element má následující atributy.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`clsid`|Požadováno. ID třídy komponenty modelu COM, vyjádřený jako identifikátor GUID.|  
|`description`|Volitelné. Název třídy.|  
|`threadingModel`|Volitelné. Model vláken používané třídy modelu COM v procesu. Pokud tato vlastnost hodnotu null, použije se bez modelu vláken. Komponenta je vytvořena na hlavním vlákně klienta a volání z jiných vláken, které jsou zařazeny do tohoto vlákna. Následující seznam uvádí platné hodnoty:<br /><br /> `Apartment`, `Free`, `Both`, a `Neutral`.|  
|`tlbid`|Volitelné. Identifikátor GUID pro knihovnu typů pro tuto součást COM.|  
|`progid`|Volitelné. Programový identifikátor závislé na verzi přidružené komponenty modelu COM Formát `ProgID` je `<vendor>.<component>.<version>`.|  
|`miscStatus`|Volitelné. Na základě informací poskytnutých manifestu duplikuje v sestavení `MiscStatus` klíč registru. Pokud hodnoty `miscStatusIcon`, `miscStatusContent`, `miscStatusDocprint`, nebo `miscStatusThumbnail` nebyly nalezeny atributy, odpovídající výchozí hodnota uvedená ve `miscStatus` se používá pro chybějící atributy. Hodnota může být čárkami oddělený seznam hodnot atributů v následující tabulce. Tento atribut lze použít, pokud třída modelu COM je OCX třída, která vyžaduje `MiscStatus` hodnoty klíčů registru.|  
|`miscStatusIcon`|Volitelné. Základě informací poskytnutých DVASPECT_ICON manifestu duplikuje v sestavení. Ikona objektu může poskytnout. Hodnota může být čárkami oddělený seznam hodnot atributů v následující tabulce. Tento atribut lze použít, pokud třída modelu COM je OCX třída, která vyžaduje `Miscstatus` hodnoty klíčů registru.|  
|`miscStatusContent`|Volitelné. Informace uvedené DVASPECT_CONTENT manifestu duplikuje v sestavení. Složený dokument zobrazitelný může poskytovat pro obrazovku nebo tiskárny. Hodnota může být čárkami oddělený seznam hodnot atributů v následující tabulce. Tento atribut lze použít, pokud třída modelu COM je OCX třída, která vyžaduje `MiscStatus` hodnoty klíčů registru.|  
|`miscStatusDocPrint`|Volitelné. Informace uvedené DVASPECT_DOCPRINT manifestu duplikuje v sestavení. Na obrazovce může poskytovat reprezentaci objektu annotable jakoby tisku na tiskárnu. Hodnota může být čárkami oddělený seznam hodnot atributů v následující tabulce. Tento atribut lze použít, pokud třída modelu COM je OCX třída, která vyžaduje `MiscStatus` hodnoty klíčů registru.|  
|`miscStatusThumbnail`|Volitelné. Informace uvedené DVASPECT_THUMBNAIL manifestu duplikuje v sestavení. Může poskytovat miniatury objektu annotable v nástroji pro procházení. Hodnota může být čárkami oddělený seznam hodnot atributů v následující tabulce. Tento atribut lze použít, pokud třída modelu COM je OCX třída, která vyžaduje `MiscStatus` hodnoty klíčů registru.|  
  
## <a name="cominterfaceexternalproxystub"></a>comInterfaceExternalProxyStub  
 `comInterfaceExternalProxyStub` Je volitelný podřízený element `file` elementu, ale může být povinný, pokud [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace obsahuje komponentu modelu COM, který chce nasadit pomocí modelu COM bez registrace Element obsahuje následující atributy.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`iid`|Požadováno. Rozhraní ID (IID), které obsluhují tento proxy server. Identifikátor IID musí mít složené závorky okolní infrastrukturou.|  
|`baseInterface`|Volitelné. Identifikátor IID rozhraní, ze kterého rozhraní odkazuje `iid` pochází.|  
|`numMethods`|Volitelné. Počet metod implementovaných rozhraní.|  
|`name`|Volitelné. Název rozhraní tak, jak se zobrazí v kódu.|  
|`tlbid`|Volitelné. Knihovna typů, která obsahuje popis rozhraní určené typem `iid` atribut.|  
|`proxyStubClass32`|Volitelné. Mapuje IID na identifikátor CLSID proxy serveru 32bitové knihovny DLL.|  
  
## <a name="cominterfaceproxystub"></a>comInterfaceProxyStub  
 `comInterfaceProxyStub` Je volitelný podřízený element `file` elementu, ale může být povinný, pokud [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace obsahuje komponentu modelu COM, který chce nasadit pomocí modelu COM bez registrace Element obsahuje následující atributy.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`iid`|Požadováno. Rozhraní ID (IID), které obsluhují tento proxy server. Identifikátor IID musí mít složené závorky okolní infrastrukturou.|  
|`baseInterface`|Volitelné. Identifikátor IID rozhraní, ze kterého rozhraní odkazuje `iid` pochází.|  
|`numMethods`|Volitelné. Počet metod implementovaných rozhraní.|  
|`Name`|Volitelné. Název rozhraní tak, jak se zobrazí v kódu.|  
|`Tlbid`|Volitelné. Knihovna typů, která obsahuje popis rozhraní určené typem `iid` atribut.|  
|`proxyStubClass32`|Volitelné. Mapuje IID na identifikátor CLSID proxy serveru 32bitové knihovny DLL.|  
|`threadingModel`|Volitelné. Volitelné. Model vláken používané třídy modelu COM v procesu. Pokud tato vlastnost hodnotu null, použije se bez modelu vláken. Komponenta je vytvořena na hlavním vlákně klienta a volání z jiných vláken, které jsou zařazeny do tohoto vlákna. Následující seznam uvádí platné hodnoty:<br /><br /> `Apartment`, `Free`, `Both`, a `Neutral`.|  
  
## <a name="windowclass"></a>windowClass  
 `windowClass` Je volitelný podřízený element `file` elementu, ale může být povinný, pokud [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace obsahuje komponentu modelu COM, který chce nasadit pomocí modelu COM bez registrace Element odkazuje na třídu okna určené komponenty modelu COM, musí mít verzi použít. Element obsahuje následující atributy.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`versioned`|Volitelné. Určuje, zda okno interní název použitý v registraci třídy obsahuje verzi sestavení, které obsahuje třídu okna ovládacích prvků. Hodnota tohoto atributu může být `yes` nebo `no`. Výchozí hodnota je `yes`. Hodnota `no` měli použít pouze v případě stejné třídy okna je definována součást vedle sebe a ekvivalentní komponenty bez –--vedle sebe a chcete je považovat za stejné třídy okna. Všimněte si, že použít obvyklé pravidla týkající se registrace tříd oken – pouze první součást, která se zaregistruje třídu okna budete moct zaregistrovat, protože nemá verzi použít.|  
  
## <a name="hash"></a>hash  
 `hash` Je volitelný podřízený element `file` elementu. `hash` Prvek nemá žádné atributy.  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] používá vylepšením hodnota hash všech souborů v aplikaci pro kontrolu zabezpečení, k zajištění, že žádné soubory byly změněny po nasazení. Pokud `hash` element není zahrnut, tato kontrola neproběhne. Proto vynechání `hash` element se nedoporučuje.  
  
 Pokud manifest obsahuje soubor, který se mají hodnotu hash, že manifestu nemůže být digitálně podepsané, protože uživatelé nemohou ověřit obsah souboru bez otisku.  
  
## <a name="dsigtransforms"></a>dsig:TRANSFORMS  
 `dsig:Transforms` Je požadovaný podřízený element `hash` elementu. `dsig:Transforms` Prvek nemá žádné atributy.  
  
## <a name="dsigtransform"></a>dsig:Transform  
 `dsig:Transform` Je požadovaný podřízený element `dsig:Transforms` elementu. `dsig:Transform` Element má následující atributy.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`Algorithm`|Algoritmus používaný k výpočtu algoritmu digest pro tento soubor. Aktuálně pouze hodnota používaná metodou [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] je `urn:schemas-microsoft-com:HashTransforms.Identity`.|  
  
## <a name="dsigdigestmethod"></a>dsig: DigestMethod  
 `dsig:DigestMethod` Je požadovaný podřízený element `hash` elementu. `dsig:DigestMethod` Element má následující atributy.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`Algorithm`|Algoritmus používaný k výpočtu algoritmu digest pro tento soubor. Aktuálně pouze hodnota používaná metodou [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] je `http://www.w3.org/2000/09/xmldsig#sha1`.|  
  
## <a name="dsigdigestvalue"></a>dsig: DigestValue  
 `dsig:DigestValue` Je požadovaný podřízený element `hash` elementu. `dsig:DigestValue` Prvek nemá žádné atributy. Jeho textová hodnota je vypočítaný algoritmus hash pro zadaný soubor.  
  
## <a name="remarks"></a>Poznámky  
 Tento prvek určuje všechny nonassembly soubory, které aplikaci tvoří a konkrétně ověření hodnoty hash souboru. Tento element může také zahrnovat data izolace modelu COM (Component Object) přidružené k souboru. Pokud se změní soubor, soubor manifestu aplikace musí být rovněž aktualizován tak, aby odrážely změny.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje `file` prvky v aplikaci manifest pro aplikace nasazené pomocí [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)].  
  
```  
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
 [ClickOnce – manifest aplikace ](../deployment/clickonce-application-manifest.md)



