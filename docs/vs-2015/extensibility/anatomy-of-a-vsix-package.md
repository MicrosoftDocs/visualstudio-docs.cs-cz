---
title: Anatomie balíčku VSIX | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- visual studio extension
- vsix
- packages
ms.assetid: 8b86d62f-c274-4e91-82e0-38cdb9a423d5
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 156b221265b4c3c23b795b09b9a50ccb27a63bcf
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295639"
---
# <a name="anatomy-of-a-vsix-package"></a>Anatomie balíčku VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSIX balíček je soubor VSIX, který obsahuje jedno nebo více rozšíření sady Visual Studio, společně s metadaty, které Visual Studio používá ke klasifikaci a instalaci rozšíření. Tato metadata jsou obsažena v manifestu VSIX a souboru [Content_Types]. XML. Balíček VSIX může také obsahovat jeden nebo více souborů s příponou. vsixlangpack pro poskytnutí lokalizovaného textu instalace a může obsahovat další balíčky VSIX pro instalaci závislostí.  
  
 Formát balíčku VSIX se řídí standardními konvencemi OPC (Open balení). Balíček obsahuje binární soubory a podpůrné soubory spolu se souborem [Content_Types]. XML a souborem manifestu. VSIX. Jeden balíček VSIX může obsahovat výstup více projektů nebo dokonce i více balíčků, které mají vlastní manifesty.  
  
> [!NOTE]
> Názvy souborů obsažených v balíčcích VSIX nesmí obsahovat mezery, ani znaky rezervované v identifikátorech URI (Uniform Resource Identifier), jak je definováno v části [\[RFC2396\]](https://go.microsoft.com/fwlink/?LinkId=90339).  
  
## <a name="the-vsix-manifest"></a>Manifest VSIX  
 Manifest VSIX obsahuje informace o rozšíření, které se má nainstalovat, a následuje po schématu VSX. Další informace najdete v referenčních informacích k [schématu rozšíření VSIX 1,0](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b). Příklad manifestu VSIX naleznete v tématu [PackageManifest element (root element, VSX Schema)](https://msdn.microsoft.com/f8ae42ba-775a-4d2b-976a-f556e147f187).  
  
 Manifest VSIX musí být pojmenován `extension.vsixmanifest`, když je obsažen v souboru VSIX.  
  
## <a name="the-content"></a>Obsah  
 Balíček VSIX může obsahovat šablony, položky nástrojů, sady VSPackage nebo jakýkoli jiný druh rozšíření, které podporuje Visual Studio.  
  
## <a name="language-packs"></a>Jazykové sady  
 Balíček VSIX může obsahovat jeden nebo více souborů s příponou. vsixlangpack k poskytnutí lokalizovaného textu během instalace. Další informace najdete v tématu [lokalizace balíčků VSIX](../extensibility/localizing-vsix-packages.md).  
  
## <a name="dependencies-and-references"></a>Závislosti a odkazy  
 VSIX balíček může obsahovat další balíčky VSIX jako odkazy. Každý z těchto dalších balíčků musí zahrnovat svůj vlastní manifest VSIX.  
  
 Pokud se uživatel pokusí nainstalovat rozšíření, které má závislosti, instalační program ověří, že požadovaná sestavení jsou nainstalována v uživatelském systému. Pokud požadovaná sestavení nejsou nalezena, **rozšíření a aktualizace** zobrazí seznam chybějících sestavení.  
  
 Pokud manifest rozšíření obsahuje jeden nebo více [referenčních](https://msdn.microsoft.com/32c52934-e81e-4b53-8cb6-4df45ef7bfa8) prvků, **rozšíření a aktualizace** porovnává manifest všech odkazů na rozšíření, která jsou nainstalována v systému, a nainstaluje odkazované rozšíření, pokud ještě není nainstalováno. Pokud je nainstalovaná starší verze odkazovaného rozšíření, novější verze ho nahradí.  
  
 Pokud projekt v řešení více projektů obsahuje odkaz na jiný projekt ve stejném řešení, balíček VSIX obsahuje závislosti daného projektu. Toto chování můžete přepsat kliknutím na odkaz na interní projekt a potom v okně **vlastnosti** nastavením **výstupních skupin zahrnutých do vlastnosti VSIX** na `BuiltProjectOutputGroup`.  
  
 Chcete-li zahrnout satelitní knihovny DLL z odkazovaných sestavení v balíčku VSIX, přidejte `SatelliteDllsProjectOutputGroup` do **výstupních skupin zahrnutých ve vlastnosti VSIX** .  
  
## <a name="installation-location"></a>Umístění instalace  
 Během instalace hledá **rozšíření a aktualizace** obsah balíčku VSIX ve složce pod%localappdata%\Microsoft\VisualStudio\14.0\Extensions.  
  
 Ve výchozím nastavení se instalace vztahuje pouze na aktuálního uživatele, protože% LocalAppData% je adresářem specifickým pro uživatele. Nicméně pokud nastavíte prvek [AllUsers](https://msdn.microsoft.com/ac817f50-3276-4ddb-b467-8bbb1432455b) manifestu na `True`, rozšíření bude nainstalováno v..\\*VisualStudioInstallationFolder*\Common7\IDE\Extensions a bude k dispozici pro všechny uživatele počítače.  
  
## <a name="content_typesxml"></a>[Content_Types]. XML  
 Soubor [Content_Types]. XML identifikuje typy souborů v rozbaleném souboru. VSIX. Sada Visual Studio používá tento soubor během instalace balíčku, ale neinstaluje samotný soubor. Další informace o tomto souboru naleznete v části [struktura souboru Content_types\]. XML](../extensibility/the-structure-of-the-content-types-dot-xml-file.md).  
  
 Soubor [Content_Types]. XML je vyžadován standardem OPC (Open balící konvence). Další informace o OPC naleznete v tématu [OPC: nový standard pro balení dat](https://go.microsoft.com/fwlink/?LinkID=148207) na webu MSDN.
