---
title: Vytvořit manifest balíčku | Microsoft Docs
description: Přečtěte si informace o použití balíčku zaváděcího nástroje k nasazení požadavků pro aplikaci ClickOnce, která obsahuje manifest balíčku pro každé národní prostředí.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- package files [Windows Installer]
- package files [ClickOnce]
- prerequisites, custom bootstrapper package
- dependencies, custom bootstrapper packages
ms.assetid: 5aecc507-2764-42f2-ae6f-c227971cf0af
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cef6cd23a1e5ff1e00e2d4d93313ee1e9355ece2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927558"
---
# <a name="how-to-create-a-package-manifest"></a>Postupy: Vytvoření manifestu balíčku
K nasazení požadavků pro aplikaci můžete použít balíček zaváděcího nástroje. Balíček zaváděcího nástroje obsahuje jeden soubor manifestu produktu, ale manifest balíčku pro každé národní prostředí. Sdílené funkce v různých lokalizovaných verzích by měly přejít k manifestu produktu.

 Další informace o manifestech produktů naleznete v tématu [How to: Create a manifest produktu](../deployment/how-to-create-a-product-manifest.md).

## <a name="create-the-package-manifest"></a>Vytvořit manifest balíčku

#### <a name="to-create-the-package-manifest"></a>Vytvoření manifestu balíčku

1. Vytvořte adresář pro balíček zaváděcího nástroje. V tomto příkladu se používá *C:\package*.

2. Vytvořte podadresář s názvem národního prostředí, například *EN* pro angličtinu.

3. V aplikaci Visual Studio vytvořte soubor XML s názvem *package.xml* a uložte jej do složky *C:\package\en* .

4. Přidejte XML pro výpis názvu balíčku zaváděcího nástroje, jazykové verze pro tento lokalizovaný manifest balíčku a volitelné licenční smlouvy. Následující kód XML používá proměnné `DisplayName` a `Culture` , které jsou definovány v pozdějším prvku.

    ```xml
    <Package
        xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
        Name="DisplayName"
        Culture="Culture"
        LicenseAgreement="eula.txt">
    ```

5. Přidejte XML pro výpis všech souborů, které jsou v adresáři specifického pro národní prostředí. Následující kód XML používá soubor s názvem *eula.txt* , který je použitelný pro národní prostředí **EN** .

    ```xml
    <PackageFiles>
      <PackageFile Name="eula.txt"/>
    </PackageFiles>
    ```

6. Přidejte XML pro definování lokalizovatelných řetězců pro balíček zaváděcího nástroje. Následující kód XML přidá chybové řetězce pro národní prostředí **EN** .

    ```xml
      <Strings>
        <String Name="DisplayName">Custom Bootstrapper Package</String>
        <String Name="CultureName">en</String>
        <String Name="NotAnAdmin">You must be an administrator to install
    this package.</String>
        <String Name="GeneralFailure">A general error has occurred while
    installing this package.</String>
    </Strings>
    ```

7. Zkopírujte složku *C:\package* do adresáře zaváděcího nástroje sady Visual Studio. V případě sady Visual Studio 2010 se jedná o adresář *\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages* .

## <a name="example"></a>Příklad
 Manifest balíčku obsahuje informace specifické pro národní prostředí, jako jsou chybové zprávy, licenční smlouvy na software a jazykové sady.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Package
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
  Name="DisplayName"
  Culture="Culture"
  LicenseAgreement="eula.txt">

  <PackageFiles>
    <PackageFile Name="eula.txt"/>
  </PackageFiles>

  <Strings>
    <String Name="DisplayName">Custom Bootstrapper Package</String>
    <String Name="Culture">en</String>
    <String Name="NotAnAdmin">You must be an administrator to install this package.</String>
    <String Name="GeneralFailure">A general error has occurred while
installing this package.</String>
  </Strings>
</Package>
```

## <a name="see-also"></a>Viz také
- [Odkaz na schéma produktu a balíčku](../deployment/product-and-package-schema-reference.md)