---
title: Anatomie balíčku VSIX | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- visual studio extension
- vsix
- packages
ms.assetid: 8b86d62f-c274-4e91-82e0-38cdb9a423d5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8a6d3f994c531bd36ab4281c5f0b27e993cd3392
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740090"
---
# <a name="anatomy-of-a-vsix-package"></a>Anatomie balíčku VSIX
Balíček VSIX je soubor *.vsix,* který obsahuje jednu nebo více rozšíření sady Visual Studio, spolu s metadaty, které Visual Studio používá ke klasifikaci a instalaci rozšíření. Tato metadata jsou obsažena v manifestu VSIX a v souboru *[Content_Types].xml.* Balíček VSIX může také obsahovat jeden nebo více souborů *Extension.vsixlangpack,* které poskytují lokalizovaný text nastavení, a může obsahovat další balíčky VSIX pro instalaci závislostí.

 Formát balíčku VSIX se řídí standardem Open Packaging Conventions (OPC). Balíček obsahuje binární soubory a podpůrné soubory spolu se souborem *[Content_Types].xml* a souborem manifestu *.vsix.* Jeden balíček VSIX může obsahovat výstup více projektů nebo dokonce více balíčků, které mají své vlastní manifesty.

> [!NOTE]
> Názvy souborů zahrnutých v balíčcích VSIX nesmí obsahovat mezery ani znaky, které jsou vyhrazeny v identifikátorech URI (Uniform Resource Identifiers), jak je definováno v části [ \[RFC2396\]](https://www.rfc-editor.org/rfc/rfc2396.txt).

## <a name="the-vsix-manifest"></a>Manifest VSIX
 Manifest VSIX obsahuje informace o rozšíření, které má být nainstalováno, a následuje schéma VSX. Další informace naleznete v [tématu VSIX rozšíření schéma 1.0 odkaz](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b). Příklad manifestu VSIX naleznete v tématu [PackageManifest element (root element, Schéma VSX).](https://msdn.microsoft.com/library/f8ae42ba-775a-4d2b-976a-f556e147f187)

 Manifest VSIX musí `extension.vsixmanifest` být pojmenován, pokud je součástí souboru ^.vsix*.

## <a name="the-content"></a>Obsah
 Balíček VSIX může obsahovat šablony, položky panelu nástrojů, vspackages nebo jakýkoli jiný druh rozšíření, který je podporován Visual Studio.

## <a name="language-packs"></a>Jazykové sady
 Balíček VSIX může obsahovat jednou nebo více souborů *Extension.vsixlangpack* poskytnout lokalizovaný text během instalace. Další informace naleznete v [tématu Lokalizace balíčků VSIX](../extensibility/localizing-vsix-packages.md).

## <a name="dependencies-and-references"></a>Závislosti a odkazy
 Balíček VSIX může obsahovat další balíčky VSIX jako odkazy. Každý z těchto dalších balíčků musí obsahovat vlastní manifest VSIX.

 Pokud se uživatel pokusí nainstalovat rozšíření, které má závislosti, instalační program ověří, zda jsou v uživatelském systému nainstalována požadovaná sestavení. Pokud nejsou nalezena požadovaná sestavení, **rozšíření a aktualizace** zobrazí seznam chybějících sestavení.

 Pokud manifest rozšíření obsahuje jeden nebo více [prvků reference,](/previous-versions/visualstudio/visual-studio-2010/dd393687(v=vs.100)) **rozšíření a aktualizace** porovná manifest každý odkaz na rozšíření, které jsou nainstalovány v systému a nainstaluje odkazované rozšíření, pokud již není nainstalován. Pokud je nainstalována starší verze odkazovaného rozšíření, nahradí ji novější verze.

 Pokud projekt v řešení více projektů obsahuje odkaz na jiný projekt ve stejném řešení, balíček VSIX obsahuje závislosti tohoto projektu. Toto chování můžete přepsat klepnutím na odkaz pro interní projekt a potom v okně **Vlastnosti** nastavením **vlastnosti Výstupní skupiny zahrnuté ve vlastnosti VSIX** na `BuiltProjectOutputGroup`.

 Chcete-li zahrnout satelitní knihovny DLL z odkazovaných `SatelliteDllsProjectOutputGroup` sestavení do balíčku VSIX, přidejte do **výstupních skupin zahrnutých do** vlastnosti VSIX.

## <a name="installation-location"></a>Umístění instalace
 Během instalace **aplikace Extensions and Updates** vyhledá obsah balíčku VSIX ve složce *%LocalAppData%\Microsoft\VisualStudio\14.0\Extensions*.

 Ve výchozím nastavení se instalace vztahuje pouze na aktuálního uživatele, protože *%LocalAppData%* je adresář specifický pro uživatele. Pokud však nastavíte prvek [AllUsers](https://msdn.microsoft.com/library/ac817f50-3276-4ddb-b467-8bbb1432455b) manifestu na `True`, bude rozšíření nainstalováno pod <em>.. \\ </em>VisualStudioInstallationFolder<em>\Common7\IDE\Extensions</em> a bude k dispozici všem uživatelům počítače.

## <a name="content_typesxml"></a>[Content_Types].xml
 Soubor *[Content_Types].xml* identifikuje typy souborů v rozšířeném souboru *Vsix.* Visual Studio používá tento soubor během instalace balíčku, ale nenainstaluje soubor sám. Další informace o tomto souboru naleznete [v tématu Struktura souboru [Content_types].xml](the-structure-of-the-content-types-dot-xml-file.md).

 Soubor *[Content_Types].xml* je vyžadován standardem Open Packaging Conventions (OPC). Další informace o OPC naleznete v [tématu OPC: Nový standard pro balení dat](https://blogs.msdn.microsoft.com/msdnmagazine/2007/08/08/opc-a-new-standard-for-packaging-your-data/) na webu MSDN.
