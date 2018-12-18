---
title: Lokalizace balíčků VSIX | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2f6bc666e244fed2bc2922ce4878434730a643e5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51750590"
---
# <a name="localizing-vsix-packages"></a>Lokalizace balíčků VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Je možné lokalizovat VSIX balíček vytvořením souboru Extension.vsixlangpack pro každý cílový jazyk a umístit je do správné složky. Při instalaci balíčku lokalizované lokalizovaný název rozšíření se zobrazí spolu s lokalizovaný popis. Pokud zadáte lokalizované licenčního souboru nebo adresu URL, která odkazuje na lokalizované informace, jsou také zobrazeny.  
  
 Pokud obsah obsahuje VSIX balíček VSPackage, která přidá příkazy nabídky nebo jiný prvek uživatelského rozhraní, přečtěte si téma [lokalizace příkazů nabídky](../extensibility/localizing-menu-commands.md) informace o lokalizaci nových prvků uživatelského rozhraní.  
  
## <a name="directory-structure"></a>Adresářová struktura  
 Když uživatel nainstaluje rozšíření, **rozšíření a aktualizace** kontroluje nejvyšší úrovni balíčku VSIX pro složku, jejíž název odpovídá národní prostředí sady Visual Studio na cílovém počítači. Pokud **rozšíření a aktualizace** najde-li .vsixlangpack souboru ve složce, nahradí lokalizované hodnoty v tomto souboru pro odpovídající hodnoty v souboru .vsixmanifest. Tyto hodnoty se zobrazí, když se instaluje rozšíření. Následující příklad ukazuje strukturu adresáře pro balíček VSIX, který je lokalizován do Španělština (es-ES) a Francouzština (fr-FR).  
  
 MyExtension.dll  
  
 Extension.vsixmanifest  
  
 [Content_Types] .xml  
  
 es-ES  
  
 Extension.vsixlangpack  
  
 fr-FR  
  
 Extension.vsixlangpack  
  
> [!NOTE]
>  Šablony projektů VSIX podporované v [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] generování manifestu VSIX a pojmenujte ho source.extension.vsixmanifest. Když Visual Studio vytvoří projekt, zkopíruje obsah tohoto souboru do Extension.VsixManifest v balíčku souboru VSIX.  
  
## <a name="the-extensionvsixlangpack-file"></a>Soubor Extension.vsixlangpack  
 Následující soubor Extension.vsixlangpack [VSIX Language Pack Schema](../extensibility/vsx-language-pack-schema-reference.md). Toto schéma je [VSIXLanguagePack](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md) kořenový element a tyto čtyři podřízených elementů: [LocalizedName](../extensibility/localizedname-element-vsix-language-pack-schema.md), [LocalizedDescription](../extensibility/localizeddescription-element-vsix-language-pack-schema.md), [MoreInfoURL](../extensibility/moreinfourl-element-vsix-language-pack-schema.md), a [licence](../extensibility/license-element-vsix-language-pack-schema.md). Tyto podřízené prvky odpovídají `Name`, `Description`, `MoreInfoURL`, a `License` podřízených elementů `Identifier` element soubor Extension.vsixmanifest.  
  
 Když vytvoříte soubor vsixlangpack, je nutné nastavit `Include in Vsix` vlastnost `true`. V opačném případě lokalizovaného instalačního text se bude ignorovat.  
  
#### <a name="to-set-the-include-in-vsix-property"></a>Chcete-li nastavit zahrnutí ve vlastnosti Vsix  
  
1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na soubor Extension.vsixlangpack a pak klikněte na tlačítko **vlastnosti**.  
  
2.  V mřížce vlastností klikněte na tlačítko **zahrnout do Vsix**a přiřadíte jí hodnotu `true`.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad ukazuje příslušné části třídy soubor Extension.vsixmanifest společně s odpovídající soubor Extension.vsixlangpack pro španělštinu. Pokud národní prostředí sady Visual Studio na cílovém počítači je nastaven na španělštinu, nahraďte hodnoty z této jazykové sady hodnot z manifestu.  
  
### <a name="code"></a>Kód  
 [Extension.vsixmanifest]  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<VSIX ...>  
  <Identifier ...>  
    <Name>Family Tree</Name>  
    <Description>This extension places a custom treeview control in the toolbox that is optimized for handling family tree information.</Description>  
    <License>EULA.rtf</License>  
    <MoreInfoURL>http://www.contoso.com/products/FamilyTree.htm</MoreInfoURL>  
    ...  
  </Identifier>  
  <References .../>  
  <Content .../>  
</VSIX>  
```  
  
 [Extension.vsixlangpack]  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<VsixLanguagePack Version="1.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema-lp/2010">  
  <LocalizedName>Arbol de Familia</LocalizedName>  
  <LocalizedDescription> Esta extensión pone control personalizado en la caja de herramientas por manejar información de familia.</LocalizedDescription>  
  <License>es\Eula.rtf</License>  
  <MoreInfoUrl> http://www.contoso.com/products/es/ArbolDeFamilia.htm</MoreInfoUrl>  
</VsixLanguagePack>  
```  
  
## <a name="see-also"></a>Viz také  
 [VSIX LanguagePack Element](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)   
 [Anatomie balíčku VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Šablona projektu VSIX](../extensibility/vsix-project-template.md)

