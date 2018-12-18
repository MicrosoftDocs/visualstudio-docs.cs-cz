---
title: 'Postupy: vytvoření manifestu produktu | Dokumentace Microsoftu'
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
- product files [ClickOnce]
- product files [Windows Installer]
- prerequisites, custom bootstrapper package
- dependencies, custom bootstrapper package
ms.assetid: 2d316aaa-8bc0-4ce5-90ab-23b3eac0b5dd
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 69ecc5e6547d84531579169ac7dcf7fcc31bc8f7
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/19/2018
ms.locfileid: "39153108"
---
# <a name="how-to-create-a-product-manifest"></a>Postupy: vytvoření manifestu produktu
Pokud chcete nasadit požadavky pro vaši aplikaci, můžete vytvořit balíček zaváděcího nástroje. Balíček zaváděcího nástroje obsahuje jeden produkt soubor manifestu ale manifest balíčku pro každé národní prostředí. Manifest balíčku obsahuje lokalizace specifických aspektů vašeho balíčku. Jedná se o řetězce, licenční smlouvy s koncovým uživatelem a jazykových sad.  
  
 Další informace o manifestech produktu najdete v tématu [postupy: vytvoření manifestu balíčku](../deployment/how-to-create-a-package-manifest.md).  
  
## <a name="create-the-product-manifest"></a>Vytvoření manifestu produktu  
  
#### <a name="to-create-the-product-manifest"></a>K vytvoření manifestu produktu  
  
1.  Vytvořte adresář pro balíček zaváděcího nástroje. Tento příklad používá C:\package.  
  
2.  V sadě Visual Studio vytvořte nový XML soubor s názvem *product.xml*a uložit ho. tím *C:\package* složky.  
  
3.  Přidejte následující kód XML pro popis kódu XML obor názvů a produktu pro balíček. Nahraďte kód produktu jedinečný identifikátor pro balíček.  
  
    ```xml  
    <Product  
    xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"   
    ProductCode="Custom.Bootstrapper.Package">  
    ```  
  
4.  Přidejte kód jazyka XML k určení, zda balíček obsahuje závislost. Tento příklad používá závislost na Microsoft Windows Installer 3.1.  
  
    ```xml  
    <RelatedProducts>  
        <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />  
      </RelatedProducts>  
    ```  
  
5.  Přidejte XML pro všechny soubory, které jsou součástí balíčku zaváděcího nástroje. Tento příklad používá název souboru balíčku *CorePackage.msi*.  
  
    ```xml  
    <PackageFiles>  
        <PackageFile Name="CorePackage.msi"/>  
    </PackageFiles>  
    ```  
  
6.  Zkopírovat nebo přesunout *CorePackage.msi* do souboru *C:\package* složky.  
  
7.  Přidejte kód jazyka XML k instalaci balíčku zaváděcího nástroje příkazů. Zaváděcí nástroj automaticky přidá **/qn** příznak, který *MSI* soubor, který bude instalaci v bezobslužném režimu. Pokud je soubor *.exe*, zaváděcí nástroj spustí *.exe* souboru prostředí. Následující kód XML ukazuje žádné argumenty *CorePackage.msi*, ale můžete vložit argument příkazového řádku do `Arguments` atribut.  
  
    ```xml  
    <Commands>  
        <Command PackageFile="CorePackage.msi" Arguments="">  
    ```  
  
8.  Přidejte následující kód XML do zkontrolujte, jestli je nainstalovaný balíček zaváděcího nástroje. Nahraďte kód produktu identifikátoru GUID distribuovatelnou komponentu.  
  
    ```xml  
    <InstallChecks>  
        <MsiProductCheck   
            Property="IsMsiInstalled"   
            Product="{XXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>  
    </InstallChecks>  
    ```  
  
9. Přidejte kód jazyka XML ke změně chování zaváděcího nástroje v závislosti na tom, jestli už je nainstalovaná komponenta zaváděcího nástroje. Pokud je součást nainstalovaná, nespustí se balíček zaváděcího nástroje. Následující kód XML kontroluje, zda je aktuální uživatel správcem, protože tato součást vyžaduje oprávnění správce.  
  
    ```xml  
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
  
    ```xml  
    <ExitCodes>  
        <ExitCode Value="0" Result="Success"/>  
        <ExitCode Value="1641" Result="SuccessReboot"/>  
        <ExitCode Value="3010" Result="SuccessReboot"/>  
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>  
    </ExitCodes>  
    ```  
  
11. Přidejte následující kód XML na konec části příkazů pro zaváděcí nástroj.  
  
    ```xml  
        </Command>  
    </Commands>  
    ```  
  
12. Přesunout *C:\package* složky zaváděcího nástroje adresáře sady Visual Studio. Pro Visual Studio 2010, je to *\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages* adresáře.  
  
## <a name="example"></a>Příklad  
 Manifest produktu obsahuje pokyny k instalaci pro vlastní požadavky.  
  
```xml  
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
  
## <a name="see-also"></a>Viz také:  
 [Referenční dokumentace schématu produktů a balíčků](../deployment/product-and-package-schema-reference.md)