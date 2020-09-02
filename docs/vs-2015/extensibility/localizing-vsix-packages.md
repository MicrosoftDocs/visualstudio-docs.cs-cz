---
title: Lokalizace balíčků VSIX | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6143b21884bc92ac79ae0fd7292a11780fec4478
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64795204"
---
# <a name="localizing-vsix-packages"></a>Lokalizace balíčků VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSIX balíček můžete lokalizovat vytvořením souboru s příponou. vsixlangpack pro každý cílový jazyk a jeho vložením do správné složky. Při instalaci lokalizovaného balíčku se lokalizovaný název rozšíření zobrazuje spolu s lokalizovaným popisem. Pokud zadáte lokalizovaný licenční soubor nebo adresu URL, která odkazuje na lokalizované informace, zobrazí se také.  
  
 Pokud obsah vašeho balíčku VSIX obsahuje VSPackage, který přidá příkazy nabídky nebo jiné uživatelské rozhraní, přečtěte si téma [lokalizace příkazů nabídky](../extensibility/localizing-menu-commands.md) pro informace o lokalizaci nových prvků uživatelského rozhraní.  
  
## <a name="directory-structure"></a>Adresářová struktura  
 Když uživatel nainstaluje rozšíření, **rozšíření a aktualizace** ověří nejvyšší úroveň balíčku VSIX pro složku, jejíž název se shoduje s národním prostředím sady Visual Studio cílového počítače. Pokud **rozšíření a aktualizace** naleznou soubor. vsixlangpack ve složce, nahradí lokalizované hodnoty v tomto souboru odpovídajícími hodnotami v souboru. vsixmanifest. Tyto hodnoty se zobrazí při instalaci rozšíření. Následující příklad ukazuje adresářovou strukturu balíčku VSIX, který je lokalizován do španělštiny (ES-ES) a francouzštiny (fr-FR).  
  
 MyExtension.dll  
  
 Přípona. vsixmanifest  
  
 [Content_Types]. XML  
  
 es-ES  
  
 Přípona. vsixlangpack  
  
 fr-FR  
  
 Přípona. vsixlangpack  
  
> [!NOTE]
> Šablony projektů podporované VSIX v [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] manifestu vygenerujte manifest VSIX a pojmenujte ho source. extension. vsixmanifest. Když Visual Studio sestaví projekt, zkopíruje obsah tohoto souboru do souboru extension. VsixManifest v balíčku VSIX.  
  
## <a name="the-extensionvsixlangpack-file"></a>Soubor Extension. vsixlangpack  
 Soubor Extension. vsixlangpack se řídí [schématem jazykové sady VSIX](../extensibility/vsx-language-pack-schema-reference.md). Toto schéma má kořenový element [VSIXLanguagePack](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md) a tyto čtyři podřízené prvky: [lokalizovaných](../extensibility/localizedname-element-vsix-language-pack-schema.md), [LocalizedDescription](../extensibility/localizeddescription-element-vsix-language-pack-schema.md), [MoreInfoURL](../extensibility/moreinfourl-element-vsix-language-pack-schema.md)a [License](../extensibility/license-element-vsix-language-pack-schema.md). Tyto podřízené prvky odpovídají `Name` `Description` `MoreInfoURL` `License` podřízeným prvkům elementu,, a v `Identifier` souboru extension. vsixmanifest.  
  
 Při vytváření souboru vsixlangpack je nutné nastavit `Include in Vsix` vlastnost na hodnotu `true` . V opačném případě bude lokalizovaný text instalace ignorován.  
  
#### <a name="to-set-the-include-in-vsix-property"></a>Nastavení vlastnosti include v souboru VSIX  
  
1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na soubor Extension. vsixlangpack a potom klikněte na příkaz **vlastnosti**.  
  
2. V mřížce vlastností klikněte na **zahrnout do VSIX**a nastavte jeho hodnotu na `true` .  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad ukazuje relevantní části souboru extension. vsixmanifest spolu s odpovídajícím souborem s příponou. vsixlangpack pro španělštinu. Hodnoty z jazykové sady nahradí hodnoty z manifestu, pokud je národní prostředí sady Visual Studio cílového počítače nastaveno na španělštinu.  
  
### <a name="code"></a>Kód  
 [Extension. vsixmanifest]  
  
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
  
 [Extension. vsixlangpack]  
  
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
 [VSIX – element elementu LanguagePack](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)   
 [Anatomie balíčku VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Šablona projektu VSIX](../extensibility/vsix-project-template.md)
