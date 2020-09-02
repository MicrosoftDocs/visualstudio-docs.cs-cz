---
title: 'Postupy: Vytvoření manifestu balíčku | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c711c50ab484cc88b1d6aff5c8e3018cead69953
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153840"
---
# <a name="how-to-create-a-package-manifest"></a>Postupy: Vytvoření manifestu balíčku
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

K nasazení požadavků pro aplikaci můžete použít balíček zaváděcího nástroje. Balíček zaváděcího nástroje obsahuje jeden soubor manifestu produktu, ale manifest balíčku pro každé národní prostředí. Sdílené funkce v různých lokalizovaných verzích by měly přejít k manifestu produktu.  
  
 Další informace o manifestech balíčků naleznete v tématu [How to: Create a manifest produktu](../deployment/how-to-create-a-product-manifest.md).  
  
## <a name="creating-the-package-manifest"></a>Vytváření manifestu balíčku  
  
#### <a name="to-create-the-package-manifest"></a>Vytvoření manifestu balíčku  
  
1. Vytvořte adresář pro balíček zaváděcího nástroje. Tento příklad používá C:\package.  
  
2. Vytvořte podadresář s názvem národního prostředí, například en pro angličtinu.  
  
3. V aplikaci Visual Studio vytvořte soubor XML s názvem `package.xml` a uložte jej do složky C:\package\en.  
  
4. Přidejte XML pro výpis názvu balíčku zaváděcího nástroje, jazykové verze pro tento lokalizovaný manifest balíčku a volitelné licenční smlouvy. Následující kód XML používá proměnné `DisplayName` a `Culture` , které jsou definovány v pozdějším prvku.  
  
    ```  
    <Package  
        xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
        Name="DisplayName"  
        Culture="Culture"  
        LicenseAgreement="eula.txt">  
    ```  
  
5. Přidejte XML pro výpis všech souborů, které jsou v adresáři specifického pro národní prostředí. Následující kód XML používá soubor s názvem eula.txt, který je použitelný pro národní prostředí **EN** .  
  
    ```  
    <PackageFiles>  
      <PackageFile Name="eula.txt"/>  
    </PackageFiles>  
    ```  
  
6. Přidejte XML pro definování lokalizovatelných řetězců pro balíček zaváděcího nástroje. Následující kód XML přidá chybové řetězce pro národní prostředí en.  
  
    ```  
      <Strings>  
        <String Name="DisplayName">Custom Bootstrapper Package</String>  
        <String Name="CultureName">en</String>  
        <String Name="NotAnAdmin">You must be an administrator to install   
    this package.</String>  
        <String Name="GeneralFailure">A general error has occurred while   
    installing this package.</String>  
    </Strings>  
    ```  
  
7. Zkopírujte složku C:\package do adresáře zaváděcího nástroje sady Visual Studio. V případě sady Visual Studio 2010 se jedná o adresář \Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages.  
  
## <a name="example"></a>Příklad  
 Manifest balíčku obsahuje informace specifické pro národní prostředí, jako jsou chybové zprávy, licenční smlouvy na software a jazykové sady.  
  
```  
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
 [Referenční schéma balíčku a produktu](../deployment/product-and-package-schema-reference.md)
