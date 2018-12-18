---
title: Vytváření balíčků bootstrapperu
ms.custom: ''
ms.date: 05/02/2018
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [Visual Studio], prerequisites
- deploying applications [Visual Studio], custom prerequisites
- prerequisites, custom
- RedistList file
- custom prerequisites
- redistributables list
ms.assetid: ba1a785b-693d-446b-bcae-b88cadee73d1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a16044657b197229253f93fc6aea6130a4522f64
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2018
ms.locfileid: "39512181"
---
# <a name="create-bootstrapper-packages"></a>Vytváření balíčků bootstrapperu
Instalační program je obecný instalační program, který můžete konfigurovat k rozpoznání a instalování distribuovatelných součástí, jako je například Instalační služby systému Windows (*MSI*) soubory a programy. Instalační program se také nazývá zaváděcí nástroj. To je programován sadou XML manifestů, které mohou specifikovat metadata pro správu instalace součásti.  Každý distribuovatelnou komponentu, nebo požadovaných součástí, která se zobrazí v **požadavky** dialogové okno pro ClickOnce je balíček zaváděcího nástroje. Balíček zaváděcího nástroje je skupina adresářů a souborů, které obsahují soubory manifestu, které popisují, jak by měly být nainstalovány kontrolu požadovaných součástí. 
  
Zaváděcí nástroj nejprve zjistí, zda některé z požadavků jsou již nainstalovány. Pokud požadavky nejsou nainstalovány, nejprve zaváděcí nástroj zobrazí licenční podmínky. Za druhé po koncový uživatel přijme podmínky licenční smlouvy, začne instalace požadavků. Jinak pokud jsou zjištěny všechny požadavky, zaváděcí nástroj pouze spustí instalační program aplikace.  
  
## <a name="create-custom-bootstrapper-packages"></a>Vytvořit vlastní balíčky zaváděcího nástroje  
Pomocí editoru jazyka XML v sadě Visual Studio můžete generovat manifesty zaváděcího nástroje. Příklad vytvoření balíčku zaváděcího nástroje naleznete v tématu [návod: vytvoření vlastního bootstrapperu s výzvou o ochraně osobních údajů](../deployment/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt.md).  
  
Vytvoření balíčku zaváděcího nástroje, jste k vytvoření manifestu produktu a, pro všechny lokalizované verze komponenty, také manifestu balíčku.
  
* Manifest produktu *product.xml*, obsahuje všechny jazykově nezávislá metadata pro balíček. Toto obsahuje metadata společná pro všechny lokalizované verze distribuovatelné součásti.  Vytvoření tohoto souboru najdete v tématu [postupy: vytvoření a Manifest produktu](../deployment/how-to-create-a-product-manifest.md).
  
* Manifest balíčku *package.xml*, obsahuje metadata pro konkrétní jazyk; obvykle obsahuje lokalizované chybové zprávy. Komponenta musí mít alespoň jeden manifest balíčku pro každou lokalizovanou verzi dané komponenty. Vytvoření tohoto souboru najdete v tématu [postupy: vytvoření balíčku Manifest](../deployment/how-to-create-a-package-manifest.md).
  
Po vytvoření těchto souborů uložte soubor manifestu produktu do složky s názvem pro vlastní zaváděcí nástroj. Soubor manifestu balíčku přejde do složky s názvem pro národní prostředí. Například pokud soubor manifestu balíčku je pro anglickou distribuci, uložte soubor do složky s názvem en. Tento proces opakujte pro každé národní prostředí, jako je například ja pro japonské písmo a de pro němčinu. Konečný vlastní balíček zaváděcího nástroje může mít následující strukturu složek.  

    ```xml
    CustomBootstrapperPackage
      product.xml
      CustomBootstrapper.msi
      de
        eula.rtf
        package.xml
      en
        eula.rtf
        package.xml
      ja
        eula.rtf
        package.xml
    ```
  
V dalším kroku zkopírujte redistribuovatelné soubory do umístění složky zaváděcího nástroje. Další informace najdete v tématu [postupy: vytvoření lokalizovaného balíčku bootstrapperu](../deployment/how-to-create-a-localized-bootstrapper-package.md).
 
    *\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages*
    
or  
    
    *\Program Files (x86)\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages*
  
Můžete také určit umístění složky zaváděcího nástroje z **cesta** hodnotu v následujícím klíči registru:  
  
    *HKLM\Software\Microsoft\GenericBootstrapper\11.0*
  
Na 64bitových systémech použijte následující klíč registru:  
  
    *HKLM\Software\Wow6432Node\Microsoft\GenericBootstrapper\11.0*
  
Každá distribuovatelná součást se zobrazí ve vlastní podsložce v adresáři balíčků. Produkt manifestu a redistribuovatelné soubory musí být vloženy do této podsložky. Lokalizované verze manifestů komponent a balíčků musí být vloženy do podsložek pojmenovaných podle jazykové.  
  
Jakmile tyto soubory budou zkopírovány do složky, balíček zaváděcího nástroje automaticky zobrazí v sadě Visual Studio **požadavky** dialogové okno. Pokud vaše vlastní balíček zaváděcího nástroje nezobrazí, zavřete a znovu otevřete **požadavky** dialogové okno. Další informace najdete v tématu [dialogové okno požadavky](../ide/reference/prerequisites-dialog-box.md).  
  
V následující tabulce jsou uvedeny vlastnosti, které jsou automaticky naplněny zaváděcím nástrojem.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|ApplicationName|Název aplikace.|  
|Vlastnost ProcessorArchitecture|Procesor a bits slova spustitelný soubor zaměřený platformy. Následující hodnoty:<br /><br /> -Intel<br />-IA64<br />– AMD64|  
|[Version9x](/windows/desktop/Msi/version9x)|Číslo verze pro operační systémy Microsoft Windows 95, Windows 98 nebo Windows ME. Syntaxe verze je Major.Minor.ServicePack.|  
|[VersionNT](/windows/desktop/Msi/versionnt)|Číslo verze pro operační systémy Windows NT, Windows 2000, Windows XP, Windows Vista, Windows Server 2008 nebo Windows 7. Syntaxe verze je Major.Minor.ServicePack.|  
|[VersionMSI](/windows/desktop/Msi/versionmsi)|Verze sestavení Instalační služby systému Windows (msi.dll) ke spuštění během instalace.|  
|[AdminUser](/windows/desktop/Msi/adminuser)|Tato vlastnost nastavena, pokud má uživatel oprávnění správce. Hodnoty jsou true nebo false.|  
|InstallMode|Režim instalace označuje, odkud je nutné komponentu nainstalovat. Následující hodnoty:<br /><br /> -HomeSite – požadavky jsou nainstalovány z webu dodavatele.<br />-SpecificSite – požadavky jsou nainstalovány z umístění, které jste vybrali.<br />-SameSite – požadavky jsou nainstalovány ze stejného umístění jako aplikace.|  
  
## <a name="separate-redistributables-from-application-installations"></a>Samostatné redistribuovatelností z instalací aplikace  
Redistribuovatelným souborům můžete zabránit v nasazení v nastavení projektů. Chcete-li to provést, vytvořte redistribuovatelný seznam ve složce RedistList v adresáři rozhraní .NET Framework:  
  
`%ProgramFiles%\Microsoft.NET\RedistList`  
  
Redistribuovatelný seznam je soubor XML, který byste měli pojmenovat pomocí následujícího formátu:  *\<název společnosti >.\< Název součásti >. RedistList.xml*. Ano, například pokud komponenta nazývá DataWidgets provedená Acme, použijte *Acme.DataWidgets.RedistList.xml*. Příklad redistribuovatelného seznamu obsahů může vypadat takto:  
  
```xml  
<?xml version="1.0" encoding="UTF-8"?>  
<FileList Redist="Acme.DataWidgets" >  
<File AssemblyName="Acme.DataGrid" Version="1.0.0.0" PublicKeyToken="b03f5f7f11d50a3a" Culture="neutral" ProcessorArchitecture="MSIL" InGAC="true" />  
</FileList>  
```  
  
## <a name="see-also"></a>Viz také:  
 [Postupy: instalace předpokladů s aplikací ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [Dialogové okno požadavky](../ide/reference/prerequisites-dialog-box.md)   
 [Referenční dokumentace schématu produktů a balíčků](../deployment/product-and-package-schema-reference.md)   
 [Použijte zaváděcí nástroj Visual Studio 2005 k zahájení instalace](http://go.microsoft.com/fwlink/?LinkId=107537)
