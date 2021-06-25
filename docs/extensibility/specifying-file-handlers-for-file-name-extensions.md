---
title: Určení obslužných rutin souborů pro přípony názvů | Microsoft Docs
description: Zjistěte, jak určit, která aplikace zpracovává příponu souboru v sadě Visual Studio SDK, pomocí OpenWithList a OpenWithProgids.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- file extensions, specifying file handlers
ms.assetid: e3de4730-a95c-465a-b3b2-92ca85364ad7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6ab370b4be8c12ad0df0c4822bcc7b487fb4aa21
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899443"
---
# <a name="specifying-file-handlers-for-file-name-extensions"></a>Určení popisovačů souborů pro přípony názvů souborů
Existuje několik způsobů, jak určit aplikaci, která zpracovává soubor s konkrétní příponou. Příkazy OpenWithList a OpenWithProgids jsou dva způsoby určení obslužných rutin souborů v položce registru pro příponu souboru.

## <a name="openwithlist-verb"></a>Příkaz OpenWithList
 Když kliknete pravým tlačítkem na soubor v Průzkumník Windows, zobrazí se **příkaz** Otevřít. Pokud je k rozšíření přidruženo více produktů, zobrazí se **podnabídka Open With (Otevřít** v aplikaci).

 Různé aplikace můžete zaregistrovat pro otevření rozšíření nastavením klíče OpenWithList pro příponu souboru v HKEY_CLASSES_ROOT. Aplikace uvedené pod tímto klíčem pro příponu souboru se zobrazí v dialogovém okně Otevřít **v** části Doporučené programy.  Následující příklad ukazuje aplikace zaregistrované k otevření přípony souboru .vcproj.

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)="VisualStudio.vcproj.14.0"
      OpenWithList\
         devenv.exe
```

> [!NOTE]
> Klíče určující aplikace jsou ze seznamu v části HKEY_CLASSES_ROOT\Applications.

 Přidáním klíče OpenWithList deklarujete, že vaše aplikace podporuje příponu souboru i v případě, že rozšíření přebírá jiná aplikace. Může to být budoucí verze vaší aplikace nebo jiné aplikace.

## <a name="openwithprogids"></a>OpenWithProgID
 Programové identifikátory (progID) jsou popisné verze identifikátorů CLASSID, které identifikují verzi aplikace nebo objektu COM. Každý objekt, který je spolu vytvořitelný, by měl mít vlastní ProgID. Například VisualStudio.DTE.7.1 spustí Visual Studio .NET 2003, zatímco VisualStudio.DTE.10.0 spustí [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Jako vlastník typu projektu nebo položky projektu musíte pro příponu souboru vytvořit ProgID pro konkrétní verzi. Tyto identifikátory ProgID mohou být redundantní v tom případě, že stejnou aplikaci může spustit více než jedno ID progid. Další informace najdete v tématu [Registrace operací pro přípony názvů souborů](../extensibility/registering-verbs-for-file-name-extensions.md).

 Pokud se chcete vyhnout duplicice při registraci od jiných dodavatelů, použijte následující zásady vytváření názvů pro progID souborů s verzí:

|Přípona souboru|ID verze ProgID|
|--------------------|----------------------|
|.extension|Productname. extension.versionMajor.versionMinor|

 Můžete registrovat různé aplikace, které mohou otevřít konkrétní příponu souboru, přidáním identifikátorů ProgID s verzí jako hodnot do klíče HKEY_CLASSES_ROOT \\ *\<extension>* \OpenWithProgids. Tento klíč registru obsahuje seznam alternativních identifikátorů PROGID přidružených k příponě souboru. Aplikace přidružené k uvedeným identifikátorům ProgID se zobrazí v **podnabídce Open With**_Product Name_ (Otevřít s názvem produktu). Pokud je stejná aplikace zadána v obou klíčích a , operační systém `OpenWithList` `OpenWithProgids` sloučí duplicity.

> [!NOTE]
> Klíč `OpenWithProgids` je podporován pouze v systému Windows XP. Vzhledem k tomu, že ostatní operační systémy tento klíč ignorují, nepoužívejte ho jako jedinou registraci obslužných rutin souborů. Tento klíč použijte k zajištění lepšího uživatelského prostředí v systému Windows XP.

 Přidejte požadované identifikátory ProgID jako hodnoty typu REG_NONE. Následující kód obsahuje příklad registrace identifikátorů ProgID pro příponu souboru (.*ext*).

```
HKEY_CLASSES_ROOT\
   .ext\
      (default)="MyProduct.ext.14.0"
      OpenWithProgids
         progid        REG_NONE (zero-length binary value)
         otherprogid   REG_NONE (zero-length binary value)
```

 ProgID zadaný jako výchozí hodnota pro příponu souboru je výchozí obslužná rutina souboru. Pokud upravíte ProgID pro příponu souboru dodané s předchozí verzí nebo , kterou mohou získat jiné aplikace, musíte klíč zaregistrovat pro vaši příponu souboru a zadat nové ProgID v seznamu spolu se starými identifikátory [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] `OpenWithProgids` ProgID, které podporujete. Příklad:

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)="VisualStudio.vcproj.14.0"
      OpenWithProgids
         vcprojfile              //old progid
         VisualStudio.vcproj.12.0 //old progid
         VisualStudio.vcproj.14.0 //new progid
```

 Pokud ke starému ProgID jsou přidružená slovesa, zobrazí se tyto příkazy také v místní nabídce v části Open **With** *Product Name* (Otevřít s názvem produktu).

## <a name="see-also"></a>Viz také
- [Přípony názvů souborů](../extensibility/about-file-name-extensions.md)
- [Registrace operací pro přípony názvů souborů](../extensibility/registering-verbs-for-file-name-extensions.md)
