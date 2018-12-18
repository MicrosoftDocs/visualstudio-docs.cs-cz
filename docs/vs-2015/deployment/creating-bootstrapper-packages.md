---
title: Vytváření balíčků Bootstrapperu | Dokumentace Microsoftu
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
manager: wpickett
ms.openlocfilehash: dcc331defab98303a805f75f75afb3e309c7d2dd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49910924"
---
# <a name="creating-bootstrapper-packages"></a>Vytváření balíčků zaváděcího nástroje
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Instalační program je obecný instalační program, který můžete konfigurovat k rozpoznání a instalování distribuovatelných součástí, jako jsou soubory Instalační služby systému Windows (.msi) a spustitelných programů. Instalační program se také nazývá zaváděcí nástroj. To je programován sadou XML manifestů, které mohou specifikovat metadata pro správu instalace součásti.  
  
 Zaváděcí nástroj nejprve zjistí, zda některé z požadavků jsou již nainstalovány. Pokud požadavky nejsou nainstalovány, nejprve zaváděcí nástroj zobrazí licenční podmínky. Za druhé po koncový uživatel přijetí licenčních smluv, začne instalace požadavků. Jinak pokud jsou zjištěny všechny požadavky, zaváděcí nástroj pouze spustí instalační program aplikace.  
  
## <a name="creating-custom-packages"></a>Vytvoření vlastních balíčků  
 Můžete generovat manifesty pomocí editoru jazyka XML v sadě Visual Studio. Další informace najdete v tématu [jak: vytvořit balíček manifestu](../deployment/how-to-create-a-package-manifest.md) a [postupy: vytvoření a Manifest produktu](../deployment/how-to-create-a-product-manifest.md). Příklad vytvoření balíčku zaváděcího nástroje naleznete v tématu [návod: vytvoření vlastního Bootstrapperu k zobrazení výzvy o ochraně osobních údajů](../deployment/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt.md).  
  
 Vytvoření balíčku zaváděcího nástroje musíte zadat redistribuovatelný balíček ve formě souboru EXE nebo MSI do generátoru manifestu zaváděcího nástroje. Generátor manifestu zaváděcího nástroje potom vytvoří následující soubory:  
  
- Manifest produktu product.xml obsahující všechny jazykově nezávislá metadata pro balíček. Toto obsahuje metadata společná pro všechny lokalizované verze distribuovatelné součásti.  
  
- Manifest balíčku package.xml, který obsahuje metadata pro konkrétní jazyk; obvykle obsahuje lokalizované chybové zprávy. Komponenta musí mít alespoň jeden manifest balíčku pro každou lokalizovanou verzi dané komponenty.  
  
  Po vytvoření těchto souborů uložte soubor manifestu produktu do složky s názvem pro vlastní zaváděcí nástroj. Soubor manifestu balíčku přejde do složky s názvem pro národní prostředí. Například pokud soubor manifestu balíčku je pro anglickou distribuci, uložte soubor do složky s názvem en. Tento proces opakujte pro každé národní prostředí, jako je například ja pro japonské písmo a de pro němčinu. Konečný vlastní balíček zaváděcího nástroje může mít následující strukturu složek.  
  
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
  
  Nakonec zkopírujte redistribuovatelné soubory do umístění složky zaváděcího nástroje. Další informace najdete v tématu [postupy: vytvoření balíčku zaváděcího nástroje lokalizované](../deployment/how-to-create-a-localized-bootstrapper-package.md).  
  
```  
\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages  
```  
  
 or  
  
```  
\Program Files (x86)\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages  
```  
  
 Můžete také určit umístění složky zaváděcího nástroje z **cesta** hodnotu v následujícím klíči registru:  
  
```  
HKLM\Software\Microsoft\GenericBootstrapper\11.0  
```  
  
 V 64bitových systémech použijte následující klíč registru:  
  
```  
HKLM\Software\Wow6432Node\Microsoft\GenericBootstrapper\11.0  
```  
  
 Každá distribuovatelná součást se zobrazí ve vlastní podsložce v adresáři balíčků. Produkt manifestu a redistribuovatelné soubory jsou vloženy do této podsložky. Lokalizované verze manifestů komponent a balíčků jsou vloženy do podsložek pojmenovaných podle jazykové.  
  
 Jakmile tyto soubory budou zkopírovány do složky zaváděcího nástroje se balíček zaváděcího nástroje automaticky zobrazí v dialogovém okně požadavky sady Visual Studio. Pokud vaše vlastní balíček zaváděcího nástroje nezobrazí, zavřete a znovu otevřete dialogové okno požadavky. Další informace najdete v tématu [dialogové okno požadavky](../ide/reference/prerequisites-dialog-box.md).  
  
 V následující tabulce jsou uvedeny vlastnosti, které jsou automaticky naplněny zaváděcím nástrojem.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|ApplicationName|Název aplikace.|  
|Vlastnost ProcessorArchitecture|Procesor a bits slova spustitelný soubor zaměřený platformy. Následující hodnoty:<br /><br /> -Intel<br />-IA64<br />– AMD64|  
|[Version9x](https://msdn.microsoft.com/library/aa372490\(v=vs.140\).aspx)|Číslo verze pro operační systémy Microsoft Windows 95, Windows 98 nebo Windows ME. Syntaxe verze je Major.Minor.ServicePack.|  
|[VersionNT](https://msdn.microsoft.com/library/aa372495\(v=vs.140\).xaspx)|Číslo verze pro operační systémy Windows NT, Windows 2000, Windows XP, Windows Vista, Windows Server 2008 nebo Windows 7. Syntaxe verze je Major.Minor.ServicePack.|  
|[VersionMSI](https://msdn.microsoft.com/library/aa372493\(v=vs.140\).aspx)|Verze sestavení Instalační služby systému Windows (msi.dll) během instalace.|  
|[AdminUser](https://msdn.microsoft.com/library/aa367545\(v=vs.140\).aspx)|Tato vlastnost nastavena, pokud má uživatel oprávnění správce. Hodnoty jsou true nebo false.|  
|InstallMode|Režim instalace označuje, odkud je nutné komponentu nainstalovat. Následující hodnoty:<br /><br /> -HomeSite – požadavky jsou nainstalovány z webu dodavatele.<br />-SpecificSite – požadavky jsou nainstalovány z umístění, které jste vybrali.<br />-SameSite – požadavky jsou nainstalovány ze stejného umístění jako aplikace.|  
  
## <a name="separating-redistributables-from-application-installations"></a>Oddělení redistribuovatelností z instalací aplikace  
 Redistribuovatelným souborům můžete zabránit v nasazení v nastavení projektů. Chcete-li to provést, vytvořte redistribuovatelný seznam ve složce RedistList v adresáři rozhraní .NET Framework:  
  
 `%ProgramFiles%\Microsoft.NET\RedistList`  
  
 Redistribuovatelný seznam je soubor XML, který byste měli pojmenovat pomocí následujícího formátu: *název společnosti*. *Název komponenty*. RedistList.xml. Ano například pokud se komponenta nazývá Datawidgets provedená Acme, použijte Acme.DataWidgets.RedistList.xml. Příklad redistribuovatelného seznamu obsahů může vypadat takto:  
  
```  
<?xml version="1.0" encoding="UTF-8"?>  
<FileList Redist="Acme.DataWidgets" >  
<File AssemblyName="Acme.DataGrid" Version="1.0.0.0" PublicKeyToken="b03f5f7f11d50a3a" Culture="neutral" ProcessorArchitecture="MSIL" InGAC="true" />  
</FileList>  
```  
  
## <a name="see-also"></a>Viz také  
 [Postupy: instalace předpokladů s aplikací ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [Dialogové okno požadavky](../ide/reference/prerequisites-dialog-box.md)   
 [Referenční schéma balíčku a produktu](../deployment/product-and-package-schema-reference.md)   
 [Použijte Visual Studio Bootstrapper 2005 k zahájení instalace](http://go.microsoft.com/fwlink/?LinkId=107537)



