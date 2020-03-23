---
title: Vytváření balíčků bootstrapperu
ms.date: 05/02/2018
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0f84f91ebedd47df8c0804adee35dcbec18d8551
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301991"
---
# <a name="create-bootstrapper-packages"></a>Vytváření balíčků bootstrapperu
Instalační program je obecný instalační program, který lze nakonfigurovat tak, aby zjišťoval a instaloval redistribuovatelné součásti, jako jsou soubory Instalační služby systému Windows (*MSI*) a spustitelné programy. Instalační program je také známý jako zaváděcí nástroj. Je naprogramován prostřednictvím sady manifestů XML, které určují metadata pro správu instalace komponenty.  Každá redistribuovatelná součást nebo předpoklad, který se zobrazí v **dialogovém okně Požadavky** pro ClickOnce je balíček zaváděcího nástroje. Balíček zaváděcího nástroje je skupina adresářů a souborů, které obsahují soubory manifestu, které popisují, jak by měl y být nainstalovány.

Zaváděcí nástroj nejprve zjistí, zda jsou některé z předpokladů již nainstalovány. Pokud nejsou nainstalovány požadavky, nejprve zaváděcí nástroj zobrazí licenční smlouvy. Za druhé, poté, co koncový uživatel přijme licenční smlouvy, instalace začne pro požadavky. V opačném případě, pokud jsou zjištěny všechny požadavky, zaváděcí nástroj pouze spustí instalační program aplikace.

## <a name="create-custom-bootstrapper-packages"></a>Vytvoření vlastních balíčků zaváděcího nástroje
Manifesty zaváděcího nástroje můžete generovat pomocí editoru XML v sadě Visual Studio. Příklad vytvoření balíčku zaváděcího nástroje najdete v [tématu Návod: Vytvoření vlastního zaváděcího nástroje s výzvou k ochraně osobních údajů](../deployment/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt.md).

Chcete-li vytvořit balíček zaváděcího nástroje, musíte vytvořit manifest produktu a pro každou lokalizovanou verzi komponenty také manifest balíčku.

* Manifest produktu *product.xml*obsahuje všechna jazykově neutrální metadata pro balíček. Obsahuje metadata společná pro všechny lokalizované verze redistribuovatelné součásti.  Chcete-li vytvořit tento soubor, přečtěte si téma [Postup: Vytvoření manifestu produktu](../deployment/how-to-create-a-product-manifest.md).

* Manifest balíčku *package package.* obvykle obsahuje lokalizované chybové zprávy. Součást musí mít alespoň jeden manifest balíčku pro každou lokalizovanou verzi této součásti. Chcete-li vytvořit tento soubor, přečtěte si téma [Postup: Vytvoření manifestu balíčku](../deployment/how-to-create-a-package-manifest.md).

Po vytvoření těchto souborů vložte soubor manifestu produktu do složky pojmenované podle vlastního zaváděcího nástroje. Soubor manifestu balíčku přejde do složky s názvem národního prostředí. Například pokud je soubor manifestu balíčku pro redistribuci v angličtině, vložte soubor do složky s názvem en. Tento postup opakujte pro každé národní prostředí, například ja pro japonštinu a de pro němčinu. Konečný vlastní zaváděcí balíček může mít následující strukturu složek.

```
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

Dále zkopírujte redistribuovatelné soubory do umístění složky zaváděcího nástroje. Další informace naleznete v [tématu Postup: Vytvoření lokalizovaného balíčku zaváděcího nástroje](../deployment/how-to-create-a-localized-bootstrapper-package.md).

```
*\Program Files (x86)\Microsoft SDKs\ClickOnce Bootstrapper*
```

nebo pro starší verze sady Visual Studio

```
*\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages*
```

– nebo –

```
*\Program Files (x86)\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages*
```

Umístění složky zaváděcího nástroje můžete také najít z hodnoty **Cesta** v následujícím klíči registru:

```
*HKLM\Software\Microsoft\GenericBootstrapper*
```

V 64bitových systémech použijte následující klíč registru:

```
*HKLM\Software\Wow6432Node\Microsoft\GenericBootstrapper*
```

Každá redistribuovatelná součást se zobrazí ve vlastní podsložce pod adresářem balíčků. Manifest produktu a redistribuovatelné soubory musí být vloženy do této podsložky. Lokalizované verze manifestů komponent a balíčků musí být umístěny do podsložek pojmenovaných podle názvu jazykové verze.

Po zkopírování těchto souborů do složky zaváděcího nástroje se balíček zaváděcího nástroje automaticky zobrazí v dialogovém okně **Požadavky** sady Visual Studio. Pokud se váš vlastní balíček zaváděcího nástroje nezobrazí, zavřete a znovu otevřete dialogové okno **Požadavky.** Další informace naleznete [v dialogovém okně Požadavky](../ide/reference/prerequisites-dialog-box.md).

V následující tabulce jsou uvedeny vlastnosti, které jsou automaticky naplněny zaváděcím nástrojem.

|Vlastnost|Popis|
|--------------|-----------------|
|ApplicationName|Název aplikace|
|ProcessorArchitecture|Procesor a bity na slovo platformy cílené spustitelný soubor. Hodnoty zahrnují následující:<br /><br /> - Intel<br />- IA64<br />- AMD64|
|[Verze9x](/windows/desktop/Msi/version9x)|Číslo verze operačních systémů Microsoft Windows 95, Windows 98 nebo Windows ME. Syntaxe verze je Major.Minor.ServicePack.|
|[VersionNT](/windows/desktop/Msi/versionnt)|Číslo verze operačních systémů Windows NT, Windows 2000, Windows XP, Windows Vista, Windows Server 2008 nebo Windows 7. Syntaxe verze je Major.Minor.ServicePack.|
|[VersionMSI](/windows/desktop/Msi/versionmsi)|Verze sestavení Instalační služby systému Windows (msi.dll), která má být spuštěna během instalace.|
|[AdminUser](/windows/desktop/Msi/adminuser)|Tato vlastnost je nastavena, pokud má uživatel oprávnění správce. Hodnoty jsou pravdivé nebo nepravdivé.|
|InstallMode|Režim instalace označuje, odkud je třeba součást nainstalovat. Hodnoty zahrnují následující:<br /><br /> - HomeSite - požadavky jsou nainstalovány z webu dodavatele.<br />- SpecificSite - požadavky jsou nainstalovány z umístění, které vyberete.<br />- SameSite - požadavky jsou instalovány ze stejného umístění jako aplikace.|

## <a name="separate-redistributables-from-application-installations"></a>Oddělení redistribuovatelných zařízení od instalací aplikací
Redistribuovatelné soubory můžete zabránit nasazení v projektech instalace. Chcete-li to provést, vytvořte redistribuovatelný seznam ve složce RedistList v adresáři rozhraní .NET Framework:

`%ProgramFiles%\Microsoft.NET\RedistList`

Redistribuovatelný seznam je soubor XML, který byste měli pojmenovat v následujícím formátu: * \<Název společnosti>.\< Název> součásti. RedistList.xml*. Pokud se tedy například komponenta nazývá DataWidgets provedené společností Acme, použijte *acme.DataWidgets.RedistList.xml*. Příklad obsahu redistribuovatelného seznamu se může podobat takto:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<FileList Redist="Acme.DataWidgets" >
<File AssemblyName="Acme.DataGrid" Version="1.0.0.0" PublicKeyToken="b03f5f7f11d50a3a" Culture="neutral" ProcessorArchitecture="MSIL" InGAC="true" />
</FileList>
```

## <a name="see-also"></a>Viz také
- [Postup: Instalace požadavků pomocí aplikace ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
- [dialogové okno Požadavky](../ide/reference/prerequisites-dialog-box.md)
- [Odkaz na schéma produktu a obalu](../deployment/product-and-package-schema-reference.md)
- [Spuštění instalace pomocí zaváděcího nástroje sady Visual Studio 2005](https://msdn.microsoft.com/magazine/cc163899.aspx)
