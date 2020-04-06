---
title: Určení obslužných rutin souborů pro přípony názvů souborů | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions, specifying file handlers
ms.assetid: e3de4730-a95c-465a-b3b2-92ca85364ad7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af195aea09c91696843c6be42c20053bb8c095a2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699757"
---
# <a name="specifying-file-handlers-for-file-name-extensions"></a>Určení popisovačů souborů pro přípony názvů souborů
Existuje několik způsobů, jak určit aplikaci, která zpracovává soubor, který má určitou příponu souboru. Slovesa OpenWithList a OpenWithProgids jsou dva způsoby, jak zadat obslužné rutiny souborů pod položkou registru pro příponu souboru.

## <a name="openwithlist-verb"></a>Sloveso OpenWithList
 Když v Průzkumníkovi Windows klepnete pravým tlačítkem myši na soubor, zobrazí se příkaz **Otevřít.** Pokud je k rozšíření přidruženo více než jeden produkt, zobrazí se podnabídka **Otevřít s.**

 Můžete zaregistrovat různé aplikace pro otevření přípony nastavením klíče OpenWithList pro příponu souboru v HKEY_CLASSES_ROOT. Aplikace uvedené pod tímto klíčem pro příponu souboru se zobrazí pod nadpisem **Doporučené programy** v **dialogovém** okně Otevřít v programu. Následující příklad ukazuje aplikace registrované k otevření přípony souboru .vcproj.

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)="VisualStudio.vcproj.14.0"
      OpenWithList\
         devenv.exe
```

> [!NOTE]
> Klíče určující aplikace jsou ze seznamu v části HKEY_CLASSES_ROOT\Aplikace.

 Přidáním klíče OpenWithList deklarujete, že vaše aplikace podporuje příponu souboru i v případě, že jiná aplikace převezme vlastnictví rozšíření. Může se jedná o budoucí verzi aplikace nebo jiné aplikace.

## <a name="openwithprogids"></a>OpenWithProgIDs
 Programatické identifikátory (ProgID) jsou popisné verze identifikátorů ClassID, které identifikují verzi aplikace nebo objektu COM. Každý kokreací objekt by měl mít svůj vlastní ProgID. Například VisualStudio.DTE.7.1 spustí Visual Studio .NET 2003 při spuštění [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]VisualStudio.DTE.10.0 . Jako vlastník typu projektu nebo typu položky projektu je nutné vytvořit propřípnu souboru specifické pro verzi. Tyto ProgID může být redundantní v tom, že více než jeden ProgID může spustit stejnou aplikaci. Další informace naleznete v [tématu Registrace sloves pro přípony názvů souborů](../extensibility/registering-verbs-for-file-name-extensions.md).

 Použijte následující konvence pojmenování pro soubor s verzí ProgID, abyste se vyhnuli duplikaci s registrací od jiných dodavatelů:

|Přípona souboru|ProgID s verzí|
|--------------------|----------------------|
|.rozšíření|Productname. extension.versionMajor.versionMinor|

 Můžete zaregistrovat různé aplikace, které jsou schopny otevřít konkrétní příponu souboru\\přidáním verzí ProgIDs jako hodnoty HKEY_CLASSES_ROOT*\<přípona>* \OpenWithProgids klíč. Tento klíč registru obsahuje seznam alternativních progidů přidružených k příponě souboru. Aplikace přidružené k uvedeným progidům se zobrazí v podnabídce **Otevřít s**_názvem produktu._ Pokud je stejná aplikace `OpenWithList` zadána v klíčích i `OpenWithProgids` v klíčích, operační systém sloučí duplikáty.

> [!NOTE]
> Klíč `OpenWithProgids` je podporován pouze v systému Windows XP. Vzhledem k tomu, že ostatní operační systémy tento klíč ignorují, nepoužívejte jej jako jedinou registraci pro obslužné rutiny souborů. Pomocí tohoto klíče můžete zajistit lepší uživatelské prostředí v systému Windows XP.

 Přidejte požadované ProgIDjako hodnoty typu REG_NONE. Následující kód obsahuje příklad registrace ProgID pro příponu souboru (.* ext*).

```
HKEY_CLASSES_ROOT\
   .ext\
      (default)="MyProduct.ext.14.0"
      OpenWithProgids
         progid        REG_NONE (zero-length binary value)
         otherprogid   REG_NONE (zero-length binary value)
```

 ProgID zadaná jako výchozí hodnota pro příponu souboru je výchozí obslužná rutina souboru. Pokud změníte ProgID pro příponu souboru, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] který byl dodán s předchozí verzí nebo které `OpenWithProgids` mohou být převzaty jinými aplikacemi, pak je nutné zaregistrovat klíč pro příponu souboru a zadat nové ProgID v seznamu spolu se starými ProgIDs, které podporujete. Například:

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)="VisualStudio.vcproj.14.0"
      OpenWithProgids
         vcprojfile              //old progid
         VisualStudio.vcproj.12.0 //old progid
         VisualStudio.vcproj.14.0 //new progid
```

 Pokud má staré ProgID slovesa přidružená, pak se tato slovesa zobrazí také v části **Otevřít s názvem** *produktu* v místní nabídce.

## <a name="see-also"></a>Viz také
- [Přípony názvů souborů](../extensibility/about-file-name-extensions.md)
- [Registrace operací pro přípony názvů souborů](../extensibility/registering-verbs-for-file-name-extensions.md)
