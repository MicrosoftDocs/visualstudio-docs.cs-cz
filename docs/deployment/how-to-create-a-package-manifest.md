---
title: 'Postupy: vytvoření manifestu balíčku | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 38a0c448bcf629c4e914393cb8eabad93ced574c
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/19/2018
ms.locfileid: "39154626"
---
# <a name="how-to-create-a-package-manifest"></a>Postupy: vytvoření manifestu balíčku
Nasazení nezbytných součástí pro vaši aplikaci, můžete balíček zaváděcího nástroje. Balíček zaváděcího nástroje obsahuje jeden produkt soubor manifestu ale manifest balíčku pro každé národní prostředí. Sdílené funkce přes různé lokalizované verze by měly patřit do manifestu produktu.  
  
 Další informace o manifestech balíčku najdete v tématu [postupy: vytvoření manifestu produktu](../deployment/how-to-create-a-product-manifest.md).  
  
## <a name="create-the-package-manifest"></a>Vytvoření manifestu balíčku  
  
#### <a name="to-create-the-package-manifest"></a>K vytvoření manifestu balíčku  
  
1.  Vytvořte adresář pro balíček zaváděcího nástroje. Tento příklad používá *C:\package*.  
  
2.  Vytvořte podadresář s názvem národního prostředí, jako například *en* pro angličtinu.  
  
3.  V sadě Visual Studio, vytvořit soubor XML, který je pojmenován *package.xml*a uložit ho. tím *C:\package\en* složky.  
  
4.  Přidejte XML pro název balíčku zaváděcího nástroje, jazykovou verzi pro tento manifest balíčku lokalizované a volitelné licenční smlouvu. Následující kód XML používá proměnné `DisplayName` a `Culture`, které jsou definovány v prvku novější.  
  
    ```xml  
    <Package  
        xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
        Name="DisplayName"  
        Culture="Culture"  
        LicenseAgreement="eula.txt">  
    ```  
  
5.  Přidejte XML pro všechny soubory, které jsou v adresáři specifických pro národní prostředí. Následující kód XML používá soubor s názvem *eula.txt* , který je možné použít **en** národní prostředí.  
  
    ```xml  
    <PackageFiles>  
      <PackageFile Name="eula.txt"/>  
    </PackageFiles>  
    ```  
  
6.  Přidejte kód jazyka XML pro definování lokalizovatelných řetězců pro balíček zaváděcího nástroje. Přidá chybové řetězce pro následující kód XML **en** národní prostředí.  
  
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
  
7.  Kopírovat *C:\package* složky zaváděcího nástroje adresáře sady Visual Studio. Pro Visual Studio 2010, je to *\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages* adresáře.  
  
## <a name="example"></a>Příklad  
 Manifest balíčku obsahuje informace o specifických pro národní prostředí, jako jsou chybové zprávy, licenční podmínky pro software a jazykových sad.  
  
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
  
## <a name="see-also"></a>Viz také:  
 [Referenční dokumentace schématu produktů a balíčků](../deployment/product-and-package-schema-reference.md)