---
title: 'Postupy: Vytvoření manifestu produktu | Microsoft Docs'
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
- product files [ClickOnce]
- product files [Windows Installer]
- prerequisites, custom bootstrapper package
- dependencies, custom bootstrapper package
ms.assetid: 2d316aaa-8bc0-4ce5-90ab-23b3eac0b5dd
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 73e2c3f2c9736fd762a9e763827ed641ea5069f7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153829"
---
# <a name="how-to-create-a-product-manifest"></a>Postupy: Vytvoření manifestu produktu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

K nasazení požadavků pro aplikaci můžete vytvořit balíček zaváděcího nástroje. Balíček zaváděcího nástroje obsahuje jeden soubor manifestu produktu, ale manifest balíčku pro každé národní prostředí. Manifest balíčku obsahuje aspekty balíčku specifické pro lokalizaci. Patří sem řetězce, licenční smlouvy s koncovým uživatelem a jazykové sady.  
  
 Další informace o manifestech produktů naleznete v tématu [How to: Create a manifest balíčku](../deployment/how-to-create-a-package-manifest.md).  
  
## <a name="creating-the-product-manifest"></a>Vytváření manifestu produktu  
  
#### <a name="to-create-the-product-manifest"></a>Vytvoření manifestu produktu  
  
1. Vytvořte adresář pro balíček zaváděcího nástroje. Tento příklad používá C:\package.  
  
2. V aplikaci Visual Studio vytvořte nový soubor XML s názvem `product.xml` a uložte jej do složky C:\package.  
  
3. Přidejte následující kód XML pro popis oboru názvů XML a kódu produktu pro balíček. Nahraďte kód produktu jedinečným identifikátorem balíčku.  
  
    ```  
    <Product  
    xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"   
    ProductCode="Custom.Bootstrapper.Package">  
    ```  
  
4. Přidejte XML, chcete-li určit, že balíček obsahuje závislost. V tomto příkladu se používá závislost na Microsoft Instalační služba systému Windows 3,1.  
  
    ```  
    <RelatedProducts>  
        <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />  
      </RelatedProducts>  
    ```  
  
5. Přidejte XML pro výpis všech souborů, které jsou v balíčku zaváděcího nástroje. V tomto příkladu se používá název souboru balíčku CorePackage.msi.  
  
    ```  
    <PackageFiles>  
        <PackageFile Name="CorePackage.msi"/>  
    </PackageFiles>  
    ```  
  
6. Zkopírujte nebo přesuňte soubor CorePackage.msi do složky C:\package.  
  
7. Přidejte XML pro instalaci balíčku pomocí příkazů zaváděcího nástroje. Zaváděcí nástroj automaticky přidá příznak **/qn** do souboru. msi, který se nainstaluje tiše. Pokud je soubor. exe, zaváděcí nástroj spustí soubor. exe pomocí prostředí. Následující kód XML ukazuje žádné argumenty pro CorePackage.msi, ale argument příkazového řádku lze vložit do atributu arguments.  
  
    ```  
    <Commands>  
        <Command PackageFile="CorePackage.msi" Arguments="">  
    ```  
  
8. Pokud chcete zjistit, jestli je tento balíček zaváděcího nástroje nainstalovaný, přidejte následující kód XML. Nahraďte kód produktu identifikátorem GUID distribuovatelné součásti.  
  
    ```  
    <InstallChecks>  
        <MsiProductCheck   
            Property="IsMsiInstalled"   
            Product="{XXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>  
    </InstallChecks>  
    ```  
  
9. Přidejte XML pro změnu chování zaváděcího nástroje v závislosti na tom, jestli je už součást zaváděcího nástroje nainstalovaná. Pokud je součást nainstalována, balíček zaváděcího nástroje se nespustí. Následující kód XML zkontroluje, zda je aktuální uživatel správcem, protože tato součást vyžaduje oprávnění správce.  
  
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
  
10. Přidejte XML pro nastavení ukončovacích kódů, pokud je instalace úspěšná a jestli je nutné restartovat počítač. Následující kód XML ukazuje ukončovací kódy chyb a FailReboot, což značí, že zaváděcí program nebude nadále instalovat balíčky.  
  
    ```  
    <ExitCodes>  
        <ExitCode Value="0" Result="Success"/>  
        <ExitCode Value="1641" Result="SuccessReboot"/>  
        <ExitCode Value="3010" Result="SuccessReboot"/>  
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>  
    </ExitCodes>  
    ```  
  
11. Přidejte následující kód XML pro konec oddílu pro příkazy zaváděcího nástroje.  
  
    ```  
        </Command>  
    </Commands>  
    ```  
  
12. Přesuňte složku C:\package do adresáře zaváděcího nástroje sady Visual Studio. V případě sady Visual Studio 2010 se jedná o adresář \Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages.  
  
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
