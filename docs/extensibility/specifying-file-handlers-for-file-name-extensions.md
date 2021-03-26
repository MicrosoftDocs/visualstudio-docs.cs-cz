---
title: Určení obslužných rutin souborů pro přípony názvů souborů | Microsoft Docs
description: Zjistěte, jak určit, která aplikace zpracovává příponu souboru v sadě Visual Studio SDK pomocí OpenWithList a OpenWithProgids.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions, specifying file handlers
ms.assetid: e3de4730-a95c-465a-b3b2-92ca85364ad7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 65705467b1531e139c0ec857d6a7b57015d5f2f9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089963"
---
# <a name="specifying-file-handlers-for-file-name-extensions"></a>Určení popisovačů souborů pro přípony názvů souborů
Existuje několik způsobů, jak určit aplikaci, která zpracovává soubor s konkrétní příponou souboru. Příkazy OpenWithList a OpenWithProgids jsou dva způsoby, jak určit obslužné rutiny souborů v položce registru pro příponu souboru.

## <a name="openwithlist-verb"></a>OpenWithList – příkaz
 Když kliknete pravým tlačítkem myši na soubor v Průzkumníkovi Windows, zobrazí se příkaz **otevřít** . Pokud je k rozšíření přidruženo více než jeden produkt, zobrazí se v podnabídce **otevřít v** příkazu.

 Můžete zaregistrovat různé aplikace a otevřít rozšíření nastavením klíče OpenWithList pro příponu souboru v HKEY_CLASSES_ROOT. Aplikace uvedené v části Tento klíč pro příponu souboru se zobrazí pod nadpisem **Doporučené programy** v dialogovém okně **otevřít v programu** . Následující příklad ukazuje aplikace zaregistrované pro otevření přípony souboru. vcproj.

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)="VisualStudio.vcproj.14.0"
      OpenWithList\
         devenv.exe
```

> [!NOTE]
> Klíče určující aplikace jsou ze seznamu v části HKEY_CLASSES_ROOT\Applications.

 Přidáním klíče OpenWithList deklarujete, že aplikace podporuje příponu souboru i v případě, že převezme vlastnictví rozšíření jiná aplikace. Může to být budoucí verze vaší aplikace nebo jiné aplikace.

## <a name="openwithprogids"></a>OpenWithProgIDs
 Programové identifikátory (ProgID) jsou popisné verze ClassIDs, které identifikují verzi aplikace nebo objektu COM. Každý společný přidaný objekt by měl mít vlastní ProgID. Například VisualStudio. DTE. 7.1 spustí Visual Studio .NET 2003 během spuštění aplikace VisualStudio. DTE. 10.0 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Jako vlastník typu projektu nebo typu položky projektu je nutné pro příponu souboru vytvořit ProgID pro konkrétní verzi. Tyto identifikátory ProgID mohou být redundantní v tom, že více než jeden identifikátor ProgID může spustit stejnou aplikaci. Další informace naleznete v tématu [registrování operací pro přípony názvů souborů](../extensibility/registering-verbs-for-file-name-extensions.md).

 Použijte následující zásady vytváření názvů souborů ProgID se správou verzí, abyste zabránili duplicitám s registrací od jiných dodavatelů:

|Přípona souboru|Identifikátor ProgID se správou verzí|
|--------------------|----------------------|
|Přípona.|NázevVýrobku. Přípona. versionMajor. versionMinor|

 Můžete zaregistrovat různé aplikace, které mohou otevřít konkrétní příponu souboru, přidáním identifikátorů ProgID s označením verze jako hodnoty do HKEY_CLASSES_ROOTho \\ *\<extension>* klíče \OpenWithProgids. Tento klíč registru obsahuje seznam alternativních identifikátorů ProgID přidružených k příponě souboru. Aplikace přidružené k uvedeným identifikátorům ProgID se zobrazí v podnabídce **otevřít s**_názvem produktu_ . Pokud je stejná aplikace zadána v obou `OpenWithList` `OpenWithProgids` klíčích a, operační systém sloučí duplicity.

> [!NOTE]
> `OpenWithProgids`Klíč je podporován pouze v systému Windows XP. Protože jiné operační systémy tento klíč ignorují, nepoužívejte ho jako jedinou registraci obslužných rutin souborů. Tento klíč použijte k zajištění lepšího uživatelského prostředí v systému Windows XP.

 Přidejte požadované identifikátory ProgID jako hodnoty typu REG_NONE. Následující kód poskytuje příklad registrace identifikátorů ProgID pro příponu souboru (.*EXT*).

```
HKEY_CLASSES_ROOT\
   .ext\
      (default)="MyProduct.ext.14.0"
      OpenWithProgids
         progid        REG_NONE (zero-length binary value)
         otherprogid   REG_NONE (zero-length binary value)
```

 Identifikátor ProgID zadaný jako výchozí hodnota pro příponu souboru je výchozí obslužná rutina souboru. Pokud změníte ProgID pro příponu souboru, která byla dodávána s předchozí verzí nástroje [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nebo kterou lze převzít přes jiné aplikace, je nutné `OpenWithProgids` klíč zaregistrovat pro příponu souboru a zadat nový identifikátor ProgID v seznamu spolu se starými identifikátory ProgID, které podporujete. Například:

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)="VisualStudio.vcproj.14.0"
      OpenWithProgids
         vcprojfile              //old progid
         VisualStudio.vcproj.12.0 //old progid
         VisualStudio.vcproj.14.0 //new progid
```

 Pokud se k původnímu identifikátoru ProgID nacházejí přidružené příkazy, pak se tyto akce zobrazí také v nabídce **otevřít s** *názvem produktu* v místní nabídce.

## <a name="see-also"></a>Viz také
- [Přípony názvů souborů](../extensibility/about-file-name-extensions.md)
- [Registrace operací pro přípony názvů souborů](../extensibility/registering-verbs-for-file-name-extensions.md)
