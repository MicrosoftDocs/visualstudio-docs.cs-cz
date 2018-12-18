---
title: 'Postupy: vytvoření manifestu produktu | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- product files [ClickOnce]
- product files [Windows Installer]
- prerequisites, custom bootstrapper package
- dependencies, custom bootstrapper package
ms.assetid: 2d316aaa-8bc0-4ce5-90ab-23b3eac0b5dd
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: fc5662763e7932cc024169969801c9c321343e32
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49270085"
---
# <a name="how-to-create-a-product-manifest"></a>Postupy: Vytvoření manifestu produktu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud chcete nasadit požadavky pro vaši aplikaci, můžete vytvořit balíček zaváděcího nástroje. Balíček zaváděcího nástroje obsahuje jeden produkt soubor manifestu ale manifest balíčku pro každé národní prostředí. Manifest balíčku obsahuje lokalizace specifických aspektů vašeho balíčku. Jedná se o řetězce, licenční smlouvy s koncovým uživatelem a jazykových sad.  
  
 Další informace o manifestech produktu najdete v tématu [postupy: vytvoření balíčku Manifest](../deployment/how-to-create-a-package-manifest.md).  
  
## <a name="creating-the-product-manifest"></a>Vytvoření manifestu produktu  
  
#### <a name="to-create-the-product-manifest"></a>K vytvoření manifestu produktu  
  
1.  Vytvořte adresář pro balíček zaváděcího nástroje. Tento příklad používá C:\package.  
  
2.  V sadě Visual Studio vytvořte nový XML soubor s názvem `product.xml`a uložte ho do složky C:\package.  
  
3.  Přidejte následující kód XML pro popis kódu XML obor názvů a produktu pro balíček. Nahraďte kód produktu jedinečný identifikátor pro balíček.  
  
    ```  
    <Product  
    xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"   
    ProductCode="Custom.Bootstrapper.Package">  
    ```  
  
4.  Přidejte kód jazyka XML k určení, zda balíček obsahuje závislost. Tento příklad používá závislost na Microsoft Windows Installer 3.1.  
  
    ```  
    <RelatedProducts>  
        <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />  
      </RelatedProducts>  
    ```  
  
5.  Přidejte XML pro všechny soubory, které jsou součástí balíčku zaváděcího nástroje. Tento příklad používá název souboru balíčku CorePackage.msi.  
  
    ```  
    <PackageFiles>  
        <PackageFile Name="CorePackage.msi"/>  
    </PackageFiles>  
    ```  
  
6.  Zkopírovat nebo přesunout soubor CorePackage.msi C:\package složky.  
  
7.  Přidejte kód jazyka XML k instalaci balíčku zaváděcího nástroje příkazů. Zaváděcí nástroj automaticky přidá **/qn** příznak, který soubor MSI, který bude instalaci v bezobslužném režimu. Pokud je soubor .exe, zaváděcí nástroj spustí soubor .exe s použitím prostředí. Následující kód XML ukazuje na CorePackage.msi žádné argumenty, ale argumentu příkazového řádku můžete umístit do argumentů atributu.  
  
    ```  
    <Commands>  
        <Command PackageFile="CorePackage.msi" Arguments="">  
    ```  
  
8.  Přidejte následující kód XML do zkontrolujte, jestli je nainstalovaný balíček zaváděcího nástroje. Nahraďte kód produktu identifikátoru GUID distribuovatelnou komponentu.  
  
    ```  
    <InstallChecks>  
        <MsiProductCheck   
            Property="IsMsiInstalled"   
            Product="{XXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>  
    </InstallChecks>  
    ```  
  
9. Přidejte kód jazyka XML ke změně chování zaváděcího nástroje v závislosti na tom, jestli už je nainstalovaná komponenta zaváděcího nástroje. Pokud je součást nainstalovaná, nespustí se balíček zaváděcího nástroje. Následující kód XML kontroluje, zda je aktuální uživatel správcem, protože tato součást vyžaduje oprávnění správce.  
  
    ```  
    <InstallConditions>  
        <BypassIf   
           Property="IsMsiInstalled"   
           Compare="ValueGreaterThan" Value="0"/>  
        <FailIf Property="AdminUser"   
            Compare="ValueNotEqualTo" Value="True"  
            String="NotAnAdmin"/>  
    </InstallConditions>  
    ```  
  
10. Přidejte kód jazyka XML pro nastavení ukončovací kód, pokud je instalace úspěšná, a pokud je nutné restartovat počítač. Následující kód XML ukazuje, že selžou a FailReboot ukončovací kódy, které označují, že zaváděcí nástroj nebude pokračovat v instalaci balíčků.  
  
    ```  
    <ExitCodes>  
        <ExitCode Value="0" Result="Success"/>  
        <ExitCode Value="1641" Result="SuccessReboot"/>  
        <ExitCode Value="3010" Result="SuccessReboot"/>  
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>  
    </ExitCodes>  
    ```  
  
11. Přidejte následující kód XML na konec části příkazů pro zaváděcí nástroj.  
  
    ```  
        </Command>  
    </Commands>  
    ```  
  
12. Přesunutí složky pro C:\package k adresáři zaváděcí nástroj Visual Studio. Pro sadu Visual Studio 2010 je to adresář SDKs\Windows\v7.0A\Bootstrapper\Packages \Program Files\Microsoft.  
  
## <a name="example"></a>Příklad  
 Manifest produktu obsahuje pokyny k instalaci pro vlastní požadavky.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<Product  
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
  ProductCode="Custom.Bootstrapper.Package">  
  
  <RelatedProducts>  
    <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />  
  </RelatedProducts>  
  
  <PackageFiles>  
    <PackageFile Name="CorePackage.msi"/>  
  </PackageFiles>  
  
  <InstallChecks>  
    <MsiProductCheck Product="IsMsiInstalled"   
      Property="{XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>  
  </InstallChecks>  
  
  <Commands>  
    <Command PackageFile="CorePackage.msi" Arguments="">  
  
      <InstallConditions>  
        <BypassIf Property="IsMsiInstalled"  
          Compare="ValueGreaterThan" Value="0"/>  
        <FailIf Property="AdminUser"   
          Compare="ValueNotEqualTo" Value="True"  
         String="NotAnAdmin"/>  
      </InstallConditions>  
  
      <ExitCodes>  
        <ExitCode Value="0" Result="Success"/>  
        <ExitCode Value="1641" Result="SuccessReboot"/>  
        <ExitCode Value="3010" Result="SuccessReboot"/>  
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>  
      </ExitCodes>  
    </Command>  
  </Commands>  
</Product>  
```  
  
## <a name="see-also"></a>Viz také  
 [Referenční schéma balíčku a produktu](../deployment/product-and-package-schema-reference.md)



