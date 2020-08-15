---
title: Anatomie balíčku VSIX | Microsoft Docs
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
ms.openlocfilehash: c52f87426b9f06ad40d77c2cc9e7be1627d2c82d
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2020
ms.locfileid: "88250825"
---
# <a name="anatomy-of-a-vsix-package"></a>Anatomie balíčku VSIX
VSIX balíček je soubor *VSIX* , který obsahuje jedno nebo více rozšíření sady Visual Studio, společně s metadaty, které Visual Studio používá ke klasifikaci a instalaci rozšíření. Tato metadata jsou obsažena v manifestu VSIX a souboru *[Content_Types]. XML* . Balíček VSIX může také obsahovat jeden nebo více souborů s *příponou. vsixlangpack* pro poskytnutí lokalizovaného textu instalace a může obsahovat další balíčky VSIX pro instalaci závislostí.

 Formát balíčku VSIX se řídí standardními konvencemi OPC (Open balení). Balíček obsahuje binární soubory a podpůrné soubory spolu se souborem *[Content_Types]. XML* a souborem manifestu *. vsix* . Jeden balíček VSIX může obsahovat výstup více projektů nebo dokonce i více balíčků, které mají vlastní manifesty.

> [!NOTE]
> Názvy souborů obsažených v balíčcích VSIX nesmí obsahovat mezery, ani znaky, které jsou vyhrazeny v identifikátorech URI (Uniform Resource Identifier), jak je definováno v [ \[ RFC2396 \] ](https://www.rfc-editor.org/rfc/rfc2396.txt).

## <a name="the-vsix-manifest"></a>Manifest VSIX
 Manifest VSIX obsahuje informace o rozšíření, které se má nainstalovat, a následuje po schématu VSX. Další informace najdete v referenčních informacích k [schématu rozšíření VSIX 1,0](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b). Příklad manifestu VSIX naleznete v tématu [PackageManifest element (root element, VSX Schema)](https://msdn.microsoft.com/library/f8ae42ba-775a-4d2b-976a-f556e147f187).

 Manifest VSIX musí být pojmenován, `extension.vsixmanifest` Pokud je obsažen v souboru ^. VSIX *.

## <a name="the-content"></a>Obsah
 Balíček VSIX může obsahovat šablony, položky nástrojů, sady VSPackage nebo jakýkoli jiný druh rozšíření, které podporuje Visual Studio.

## <a name="language-packs"></a>Jazykové sady
 Balíček VSIX může obsahovat jeden nebo více souborů s *příponou. vsixlangpack* k poskytnutí lokalizovaného textu během instalace. Další informace najdete v tématu [lokalizace balíčků VSIX](../extensibility/localizing-vsix-packages.md).

## <a name="dependencies-and-references"></a>Závislosti a odkazy
 VSIX balíček může obsahovat další balíčky VSIX jako odkazy. Každý z těchto dalších balíčků musí zahrnovat svůj vlastní manifest VSIX.

 Pokud se uživatel pokusí nainstalovat rozšíření, které má závislosti, instalační program ověří, že požadovaná sestavení jsou nainstalována v uživatelském systému. Pokud požadovaná sestavení nejsou nalezena, **rozšíření a aktualizace** zobrazí seznam chybějících sestavení.

 Pokud manifest rozšíření obsahuje jeden nebo více [referenčních](/previous-versions/visualstudio/visual-studio-2010/dd393687(v=vs.100)) prvků, **rozšíření a aktualizace** porovnává manifest všech odkazů na rozšíření, která jsou nainstalována v systému, a nainstaluje odkazované rozšíření, pokud ještě není nainstalováno. Pokud je nainstalovaná starší verze odkazovaného rozšíření, novější verze ho nahradí.

 Pokud projekt v řešení více projektů obsahuje odkaz na jiný projekt ve stejném řešení, balíček VSIX obsahuje závislosti daného projektu. Toto chování můžete přepsat tak, že vyberete odkaz pro interní projekt a potom v okně **vlastnosti** nastavíte **výstupní skupiny zahrnuté do vlastnosti VSIX** na `BuiltProjectOutputGroup` .

 Chcete-li zahrnout satelitní knihovny DLL z odkazovaných sestavení v balíčku VSIX, přidejte `SatelliteDllsProjectOutputGroup` do **výstupních skupin obsažených ve vlastnostech VSIX** .

## <a name="installation-location"></a>Umístění instalace
 Během instalace vyhledá **rozšíření a aktualizace** obsah balíčku VSIX ve složce v rámci *%localappdata%\Microsoft\VisualStudio\14.0\Extensions*.

 Ve výchozím nastavení se instalace vztahuje pouze na aktuálního uživatele, protože *% localappdata%* je adresářem specifickým pro uživatele. Nicméně pokud nastavíte element [AllUsers](https://msdn.microsoft.com/library/ac817f50-3276-4ddb-b467-8bbb1432455b) manifestu na `True` , bude rozšíření nainstalováno v <em>.. \\ </em> VisualStudioInstallationFolder<em>\Common7\IDE\Extensions</em> a budou k dispozici pro všechny uživatele počítače.

## <a name="content_typesxml"></a>[Content_Types]. XML
 Soubor *[Content_Types]. XML* identifikuje typy souborů v rozbaleném souboru *. vsix* . Sada Visual Studio používá tento soubor během instalace balíčku, ale neinstaluje samotný soubor. Další informace o tomto souboru naleznete v tématu [struktura souboru [Content_Types]. XML](the-structure-of-the-content-types-dot-xml-file.md).

 Soubor *[Content_Types]. XML* je vyžadován standardem OPC (Open balící konvence). Další informace o OPC naleznete v tématu [OPC: nový standard pro balení dat](https://blogs.msdn.microsoft.com/msdnmagazine/2007/08/08/opc-a-new-standard-for-packaging-your-data/) na webu MSDN.
