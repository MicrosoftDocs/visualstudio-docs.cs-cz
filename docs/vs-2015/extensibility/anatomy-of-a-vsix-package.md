---
title: Anatomie balíčku VSIX | Dokumentace Microsoftu
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
- visual studio extension
- vsix
- packages
ms.assetid: 8b86d62f-c274-4e91-82e0-38cdb9a423d5
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e1534c13c6c09a95fab21582ba0016153d1a6992
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51806981"
---
# <a name="anatomy-of-a-vsix-package"></a>Anatomie balíčku VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Balíček VSIX je souboru .vsix, který obsahuje jeden nebo více rozšíření sady Visual Studio spolu s metadaty, který sada Visual Studio používá ke klasifikaci a nainstalovat rozšíření. Tato metadata jsou obsaženy v manifestu VSIX a souboru [Content_Types] .xml. Balíčku VSIX může obsahovat také jeden nebo více souborů Extension.vsixlangpack poskytnout textu lokalizované instalace a může obsahovat další balíčky VSIX nainstalovat závislosti.  
  
 Formát balíčku VSIX dodržuje standardní konvence Open Packaging (OPC). Balíček obsahuje binární soubory a podpůrné soubory, společně s souboru [Content_Types] .xml a .vsix soubor manifestu. Jeden VSIX balíček může obsahovat výstupu více projektů nebo dokonce více balíčků, které mají své vlastní manifest.  
  
> [!NOTE]
>  Názvy souborů součástí balíčků VSIX nesmí obsahovat mezery ani znaky, které jsou vyhrazené v identifikátory URI (Uniform Resource), jako jsou definované v části [ \[RFC2396\]](http://go.microsoft.com/fwlink/?LinkId=90339).  
  
## <a name="the-vsix-manifest"></a>VSIX Manifest  
 VSIX manifest obsahuje informace o rozšíření k instalaci a způsobem VSX schématu. Další informace najdete v tématu [odkaz 1.0 schématu rozšíření VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b). Manifest VSIX příklad naleznete v tématu [PackageManifest – Element (kořenový Element, schéma VSX)](http://msdn.microsoft.com/en-us/f8ae42ba-775a-4d2b-976a-f556e147f187).  
  
 VSIX manifest musí mít název `extension.vsixmanifest` když je zahrnutý v souboru .vsix.  
  
## <a name="the-content"></a>Obsah  
 Balíčku VSIX může obsahovat šablony, položky panelu nástrojů, rozšíření VSPackages nebo jakékoli jiné rozšíření, které podporuje Visual Studio.  
  
## <a name="language-packs"></a>Jazykové sady  
 Balíčku VSIX může obsahovat jednou nebo více souborů Extension.vsixlangpack poskytnout lokalizovanému textu během instalace. Další informace najdete v tématu [lokalizace balíčků VSIX](../extensibility/localizing-vsix-packages.md).  
  
## <a name="dependencies-and-references"></a>Závislosti a odkazy  
 Balíčku VSIX může obsahovat další balíčky VSIX jako odkazy. Každá z těchto balíčků musí obsahovat manifestu VSIX.  
  
 Pokud se uživatel pokusí nainstalovat rozšíření, která obsahuje závislosti, instalační služba zkontroluje, že požadovaná sestavení jsou nainstalovány v systému uživatele. Pokud nejsou požadované sestavení nalezeno, **rozšíření a aktualizace** zobrazí seznam chybějících sestavení.  
  
 Pokud manifest rozšíření obsahuje jeden nebo více [odkaz](http://msdn.microsoft.com/en-us/32c52934-e81e-4b53-8cb6-4df45ef7bfa8) prvky, **rozšíření a aktualizace** porovná manifestu každý odkaz na rozšíření, které jsou nainstalované v systému a nainstaluje odkazované rozšíření, pokud ještě není nainstalovaná. Pokud je nainstalovaná starší verze odkazovaného rozšíření, nahradí jej na novější verzi.  
  
 Pokud projekt ve víceprojektové řešení obsahuje odkaz na jiný projekt ve stejném řešení, balíčku VSIX obsahuje závislosti projektu. Toto chování můžete přepsat kliknutím na odkaz pro interní projekt a pak v **vlastnosti** okno nastavení **výstupní skupiny součástí VSIX** vlastnost `BuiltProjectOutputGroup`.  
  
 Chcete-li zahrnout satelitní knihovny DLL z odkazovaných sestavení v balíčku souboru VSIX, přidejte `SatelliteDllsProjectOutputGroup` k **výstupní skupiny součástí VSIX** vlastnost.  
  
## <a name="installation-location"></a>Umístění instalace  
 Během instalace **rozšíření a aktualizace** hledá obsah balíčku VSIX do složky v klíči registru % LocalAppData%\Microsoft\VisualStudio\14.0\Extensions.  
  
 Ve výchozím nastavení instalaci platí pouze pro aktuálního uživatele, protože % LocalAppData % je adresář specifické pro uživatele. Ale pokud nastavíte [AllUsers](http://msdn.microsoft.com/en-us/ac817f50-3276-4ddb-b467-8bbb1432455b) elementu v manifestu do `True`, nainstaluje rozšíření v části... \\ *VisualStudioInstallationFolder*\Common7\IDE\Extensions a bude k dispozici pro všechny uživatele počítače.  
  
## <a name="contenttypesxml"></a>[Content_Types] .xml  
 Souboru [Content_Types] .xml určuje typy souborů v souboru .vsix rozbalený. Tento soubor používá při instalaci balíčku Visual Studio, ale není možné nainstalovat samotný soubor. Další informace o tomto souboru najdete v tématu [struktura Content_types\]XML soubor](../extensibility/the-structure-of-the-content-types-dot-xml-file.md).  
  
 Podle otevřené balení konvence (OPC) standard se vyžaduje souboru [Content_Types] .xml. Další informace o OPC, naleznete v tématu [OPC: A nový standardní pro vytváření balíčků dat](http://go.microsoft.com/fwlink/?LinkID=148207) na webové stránce MSDN.

