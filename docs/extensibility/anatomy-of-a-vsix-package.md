---
title: Anatomie balíčku VSIX | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- visual studio extension
- vsix
- packages
ms.assetid: 8b86d62f-c274-4e91-82e0-38cdb9a423d5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1dea0fce75d83678161013baef109364842fcc46
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49937730"
---
# <a name="anatomy-of-a-vsix-package"></a>Anatomie balíčku VSIX
Je balíčku VSIX *VSIX* soubor, který obsahuje jeden nebo více rozšíření sady Visual Studio spolu s metadaty sady Visual Studio používá ke klasifikaci a nainstalovat rozšíření. Tato metadata jsou obsaženy v manifestu VSIX a *[Content_Types] .xml* souboru. Balíčku VSIX může obsahovat také jeden nebo více *Extension.vsixlangpack* soubory k poskytování lokalizované textu instalace a může obsahovat další balíčky VSIX nainstalovat závislosti.  
  
 Formát balíčku VSIX dodržuje standardní konvence Open Packaging (OPC). Balíček obsahuje binární soubory a podpůrné soubory, spolu s *[Content_Types] .xml* souboru a *VSIX* soubor manifestu. Jeden VSIX balíček může obsahovat výstupu více projektů nebo dokonce více balíčků, které mají své vlastní manifest.  
  
> [!NOTE]
>  Názvy souborů součástí balíčků VSIX nesmí obsahovat mezery ani znaky, které jsou vyhrazené v identifikátory URI (Uniform Resource), jako jsou definované v části [ \[RFC2396\]](http://go.microsoft.com/fwlink/?LinkId=90339).  
  
## <a name="the-vsix-manifest"></a>VSIX manifest  
 VSIX manifest obsahuje informace o rozšíření k instalaci a způsobem VSX schématu. Další informace najdete v tématu [referenční dokumentace schématu 1.0 rozšíření VSIX](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b). Manifest VSIX příklad naleznete v tématu [PackageManifest – element (kořenový element, schéma VSX)](https://msdn.microsoft.com/library/f8ae42ba-775a-4d2b-976a-f556e147f187).  
  
 VSIX manifest musí mít název `extension.vsixmanifest` když je součástí ^ soubor .vsix *.  
  
## <a name="the-content"></a>Obsah  
 Balíčku VSIX může obsahovat šablony, položky panelu nástrojů, rozšíření VSPackages nebo jakékoli jiné rozšíření, které podporuje Visual Studio.  
  
## <a name="language-packs"></a>Jazykové sady  
 Balíčku VSIX může obsahovat jedno nebo více *Extension.vsixlangpack* soubory k poskytování lokalizovanému textu během instalace. Další informace najdete v tématu [balíčků VSIX lokalizace](../extensibility/localizing-vsix-packages.md).  
  
## <a name="dependencies-and-references"></a>Závislosti a odkazy  
 Balíčku VSIX může obsahovat další balíčky VSIX jako odkazy. Každá z těchto balíčků musí obsahovat manifestu VSIX.  
  
 Pokud se uživatel pokusí nainstalovat rozšíření, která obsahuje závislosti, instalační služba zkontroluje, že požadovaná sestavení jsou nainstalovány v systému uživatele. Pokud nejsou požadované sestavení nalezeno, **rozšíření a aktualizace** zobrazí seznam chybějících sestavení.  
  
 Pokud manifest rozšíření obsahuje jeden nebo více [odkaz](/previous-versions/visualstudio/visual-studio-2010/dd393687(v=vs.100)) prvky, **rozšíření a aktualizace** porovná manifestu každý odkaz na rozšíření, které jsou nainstalované v systému a nainstaluje odkazované rozšíření, pokud ještě není nainstalovaná. Pokud je nainstalovaná starší verze odkazovaného rozšíření, nahradí jej na novější verzi.  
  
 Pokud projekt ve víceprojektové řešení obsahuje odkaz na jiný projekt ve stejném řešení, balíčku VSIX obsahuje závislosti projektu. Toto chování můžete přepsat kliknutím na odkaz pro interní projekt a pak v **vlastnosti** okno nastavení **výstupní skupiny součástí VSIX** vlastnost `BuiltProjectOutputGroup`.  
  
 Chcete-li zahrnout satelitní knihovny DLL z odkazovaných sestavení v balíčku souboru VSIX, přidejte `SatelliteDllsProjectOutputGroup` k **výstupní skupiny součástí VSIX** vlastnost.  
  
## <a name="installation-location"></a>Umístění instalace  
 Během instalace **rozšíření a aktualizace** hledá obsah balíčku VSIX v rámci *%LocalAppData%\Microsoft\VisualStudio\14.0\Extensions*.  
  
 Ve výchozím nastavení, instalaci platí pouze pro aktuálního uživatele, protože *% LocalAppData %* je adresář specifické pro uživatele. Ale pokud nastavíte [AllUsers](https://msdn.microsoft.com/library/ac817f50-3276-4ddb-b467-8bbb1432455b) elementu v manifestu do `True`, nainstaluje rozšíření v rámci <em>... \\</em> VisualStudioInstallationFolder<em>\Common7\IDE\Extensions</em> a bude k dispozici pro všechny uživatele počítače.  
  
## <a name="contenttypesxml"></a>[Content_Types] .xml  
 *[Content_Types] .xml* souboru Určuje typy souborů v rozbalených *VSIX* souboru. Tento soubor používá při instalaci balíčku Visual Studio, ale není možné nainstalovat samotný soubor. Další informace o tomto souboru najdete v tématu [struktura souboru [Content_types] .xml](the-structure-of-the-content-types-dot-xml-file.md).  
  
 A *[Content_Types] .xml* vyžaduje soubor standardu Open Packaging konvence OPC (). Další informace o OPC, naleznete v tématu [OPC: novým standardem pro vytváření balíčků dat](https://blogs.msdn.microsoft.com/msdnmagazine/2007/08/08/opc-a-new-standard-for-packaging-your-data/) na webové stránce MSDN.