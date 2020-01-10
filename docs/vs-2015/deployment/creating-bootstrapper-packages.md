---
title: Vytváření balíčků zaváděcího nástroje | Microsoft Docs
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
- deploying applications [Visual Studio], prerequisites
- deploying applications [Visual Studio], custom prerequisites
- prerequisites, custom
- RedistList file
- custom prerequisites
- redistributables list
ms.assetid: ba1a785b-693d-446b-bcae-b88cadee73d1
caps.latest.revision: 47
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: daf72a4466cd0f02eb6ef3a357276ed690fd26bf
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75845524"
---
# <a name="creating-bootstrapper-packages"></a>Vytváření balíčků zaváděcího nástroje
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Instalační program je obecný instalační program, který se dá nakonfigurovat tak, aby zjišťoval a instaloval distribuovatelné součásti, jako jsou soubory Instalační služba systému Windows (. msi) a spustitelné programy. Instalační program je také označován jako zaváděcí nástroj. Je naprogramován sadou manifestů XML, které určují metadata pro správu instalace součásti.  
  
 Zaváděcí nástroj nejprve zjistí, zda některé z požadovaných součástí jsou již nainstalovány. Pokud požadavky nejsou nainstalovány, nejprve si zaváděcí nástroj zobrazí licenční smlouvy. Za druhé se po přijetí licenčních smluv koncovým uživatelem spustí instalace požadovaných součástí. V opačném případě, pokud jsou zjištěny všechny požadavky, zaváděcí nástroj pouze spustí instalační program aplikace.  
  
## <a name="creating-custom-packages"></a>Vytváření vlastních balíčků  
 Manifesty můžete vygenerovat pomocí editoru XML v aplikaci Visual Studio. Další informace najdete v tématech [Postup: Vytvoření manifestu balíčku](../deployment/how-to-create-a-package-manifest.md) a [Postup: Vytvoření manifestu produktu](../deployment/how-to-create-a-product-manifest.md). Příklad vytvoření balíčku zaváděcího nástroje najdete v tématu [Návod: Vytvoření vlastního zaváděcího nástroje pro zobrazení výzvy k ochraně osobních údajů](../deployment/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt.md).  
  
 Chcete-li vytvořit balíček zaváděcího nástroje, je nutné dodat distribuovatelné ve formě souboru EXE nebo MSI file.to generátor manifestu zaváděcího nástroje. Generátor manifestu zaváděcího nástroje pak vytvoří následující soubory:  
  
- Manifest produktu Product. XML, který obsahuje libovolná jazykově neutrální metadata balíčku. Obsahuje metadata společná pro všechny lokalizované verze distribuovatelné součásti.  
  
- Manifest balíčku Package. XML, který obsahuje metadata specifická pro jazyk; obvykle obsahuje lokalizované chybové zprávy. Komponenta musí mít alespoň jeden manifest balíčku pro každou lokalizovanou verzi této součásti.  
  
  Po vytvoření těchto souborů vložte soubor manifestu produktu do složky s názvem pro vlastní zaváděcí nástroj. Soubor manifestu balíčku přejde do složky s názvem pro národní prostředí. Například pokud je soubor manifestu balíčku pro anglickou distribuci, uložte soubor do složky s názvem en. Tento postup opakujte pro každé národní prostředí, například ja pro japonštinu a de pro němčinu. Konečný balíček vlastního zaváděcího nástroje může mít následující strukturu složek.  
  
  `CustomBootstrapperPackage`  
  
  `product.xml`  
  
  `CustomBootstrapper.msi`  
  
  `de`  
  
  `eula.rtf`  
  
  `package.xml`  
  
  `en`  
  
  `eula.rtf`  
  
  `package.xml`  
  
  `ja`  
  
  `eula.rtf`  
  
  `package.xml`  
  
  Nakonec zkopírujte redistribuovatelné soubory do umístění složky zaváděcího nástroje. Další informace naleznete v tématu [How to: Create a lokalizovaný balíček zaváděcího nástroje](../deployment/how-to-create-a-localized-bootstrapper-package.md).  
  
```  
\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages  
```  
  
 nebo  
  
```  
\Program Files (x86)\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages  
```  
  
 Umístění složky zaváděcího nástroje můžete také určit z hodnoty **cesty** v následujícím klíči registru:  
  
```  
HKLM\Software\Microsoft\GenericBootstrapper\11.0  
```  
  
 V 64 bitových systémech použijte následující klíč registru:  
  
```  
HKLM\Software\Wow6432Node\Microsoft\GenericBootstrapper\11.0  
```  
  
 Každá Distribuovatelný součást se zobrazí ve své vlastní podsložce v adresáři Packages. Manifest produktu a redistribuovatelné soubory jsou vloženy do této podsložky. Lokalizované verze manifestů komponent a balíčků jsou umístěny v podsložkách s názvem podle názvu jazykové verze.  
  
 Po zkopírování těchto souborů do složky zaváděcího nástroje se balíček zaváděcího nástroje automaticky zobrazí v dialogovém okně předpoklady sady Visual Studio. Pokud se vlastní balíček zaváděcího nástroje nezobrazí, zavřete a znovu otevřete dialogové okno požadavky. Další informace najdete v [dialogovém okně předpoklady](../ide/reference/prerequisites-dialog-box.md).  
  
 V následující tabulce jsou uvedeny vlastnosti, které zaváděcí nástroj automaticky vyplní.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|ApplicationName|Název aplikace|  
|ProcessorArchitecture|Procesor a bity na slova platformy, na kterou cílí spustitelný soubor. Mezi hodnoty patří následující:<br /><br /> – Intel<br />– IA64<br />– AMD64|  
|[Version9x](https://msdn.microsoft.com/library/aa372490\(v=vs.140\).aspx)|Číslo verze pro operační systémy Microsoft Windows 95, Windows 98 nebo Windows MILLENNIUM. Syntaxe verze je hlavní_verze. podverze. ServicePack.|  
|[VersionNT](/windows/desktop/Msi/versionnt)|Číslo verze pro operační systémy Windows NT, Windows 2000, Windows XP, Windows Vista, Windows Server 2008 nebo Windows 7. Syntaxe verze je hlavní_verze. podverze. ServicePack.|  
|[VersionMSI](https://msdn.microsoft.com/library/aa372493\(v=vs.140\).aspx)|Verze sestavení Instalační služba systému Windows (MSI. dll) se spouští během instalace.|  
|[AdminUser](https://msdn.microsoft.com/library/aa367545\(v=vs.140\).aspx)|Tato vlastnost je nastavena, pokud má uživatel oprávnění správce. Hodnoty jsou true nebo false.|  
|InstallMode|Režim instalace označuje, odkud je nutné součást nainstalovat. Mezi hodnoty patří následující:<br /><br /> -HomeSite – požadavky jsou nainstalovány z webu dodavatele.<br />-SpecificSite – požadavky jsou nainstalovány z umístění, které jste vybrali.<br />-SameSite – požadavky jsou nainstalovány ze stejného umístění jako aplikace.|  
  
## <a name="separating-redistributables-from-application-installations"></a>Oddělení redistribuovatelných instalací aplikací  
 Můžete zabránit nasazení vašich redistribuovatelných souborů v projektech instalace. K tomu je potřeba vytvořit Distribuovatelný seznam ve složce RedistList v adresáři .NET Framework:  
  
 `%ProgramFiles%\Microsoft.NET\RedistList`  
  
 Distribuovatelný seznam je soubor XML, který byste měli pojmenovat v následujícím formátu: *název společnosti*. *Název součásti* RedistList. XML. Takže pokud se například komponenta nazývá DataWidgets vytvořená Acme, použijte Acme. DataWidgets. RedistList. XML. Příklad redistribuovatelného seznamu obsahu může vypadat takto:  
  
```  
<?xml version="1.0" encoding="UTF-8"?>  
<FileList Redist="Acme.DataWidgets" >  
<File AssemblyName="Acme.DataGrid" Version="1.0.0.0" PublicKeyToken="b03f5f7f11d50a3a" Culture="neutral" ProcessorArchitecture="MSIL" InGAC="true" />  
</FileList>  
```  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Instalace předpokladů s aplikací ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [Dialogové okno předpoklady](../ide/reference/prerequisites-dialog-box.md)   
 [Referenční  schématu produktu a balíčku](../deployment/product-and-package-schema-reference.md)  
 [Použití zaváděcího nástroje sady Visual Studio 2005 k zahájení instalace](https://msdn.microsoft.com/magazine/cc163899.aspx)
