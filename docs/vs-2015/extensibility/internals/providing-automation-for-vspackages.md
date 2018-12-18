---
title: Poskytování automatizace pro balíčky VSPackages | Dokumentace Microsoftu
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
- VSPackages, automation [Visual Studio SDK]
- automation [Visual Studio SDK], VSPackages
ms.assetid: 104c4c55-78b8-42f4-b6b0-9a334101aaea
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fc6eb16d1873c7986d9fac556440f24eb007396f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51774169"
---
# <a name="providing-automation-for-vspackages"></a>Poskytování automatizace pro balíčky VSPackages
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Existují dva hlavní způsoby poskytování automatizace pro vaše rozšíření VSPackages: implementací objektů specifických pro balíček VSPackage správy kódu a implementací standardní automatizační objekty. Obecně platí ty se používají společně k rozšíření modelu automatizace prostředí.  
  
## <a name="vspackage-specific-objects"></a>Objekty specifické VSPackage  
 Některých místech v rámci modelu automatizace vyžadují, abyste poskytují objekty automatizace, které jsou jedinečné pro vaše VSPackage. Například nové projekty vyžadují různé objekty, které obsahuje pouze vašeho balíčku VSPackage. Názvy těchto objektů jsou uloženy do registru a získali prostřednictvím volání do prostředí `DTE` objektu.  
  
 VSPackage specifické objekty, nejde získat také při spotřebitel automation používá objekt poskytnutý prostřednictvím vlastnosti objektu standardní objektu. Například standardní `Window` objekt má `Object` vlastnost, běžně označované jako `Windows.Object` vlastnost. Při volání spotřebitelů `Window.Object` okna implementované v vašeho balíčku VSPackage, předáte zpět konkrétní automatizační objekt vlastní návrh.  
  
#### <a name="projects"></a>Projekty  
 Model automatizace pro nové typy projektů pomocí vlastní VSPackage specifické objekty, které můžete rozšířit rozšíření VSPackages. Hlavním účelem poskytnutí nových objektů automatizace pro vaše VSPackage je rozlišit projektu jedinečný objekty z <xref:Microsoft.VisualStudio.VCProjectEngine.VCProject> nebo <xref:VSLangProj80.VSProject2> objektu. Toto rozlišení je užitečné, pokud byste chtěli poskytnout způsob, jak jednoduché nebo iteraci vašeho typu projektu kromě jiných typů projektů by se zobrazují vedle sebe v řešení. Další informace najdete v tématu [zveřejnění objekty projektu](../../extensibility/internals/exposing-project-objects.md).  
  
#### <a name="events"></a>Události  
 Architektura události prostředí nabízí další místo, kde můžete přidat vlastní VSPackage konkrétní objekty. Tím, že vytvoříte vlastní objekty jedinečný událostí, je možné rozšířit model událostí prostředí pro projekty. Můžete chtít poskytnout vlastní události, když do své vlastní typ projektu se přidá nová položka. Další informace najdete v tématu [vystavení události](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md).  
  
#### <a name="window-objects"></a>Objekty oken  
 Windows můžete předat zpět objekt automatizace specifické pro VSPackage zpět do prostředí při volání. Můžete implementovat objekt, který je odvozen z <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>, <xref:EnvDTE.IExtensibleObject> nebo `IDispatch` , která předá zpět vlastnosti rozšíření objekt okna, ve kterém je umístěn. Například můžete použít tento přístup k poskytování automatizace pro ovládací prvek umístěný v rámci okna. Sémantika tento objekt a všechny další objekty, které může prodloužit jsou do návrhu. Další informace najdete v tématu [jak: poskytuje automatizaci pro Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md).  
  
#### <a name="options-pages-on-the-tools-menu"></a>Stránky možnosti v nabídce Nástroje  
 Můžete vytvořit stránky, které rozšiřují nástroje, možnosti modelu automatizace prostřednictvím implementace stránky a přidání informací do registru a vytvořit vlastní možnosti. Vaše stránky může být volána prostřednictvím objektového modelu prostředí jako jakékoli jiné stránky možnosti. Vyžaduje-li návrh funkce, kterou chcete přidat do prostředí prostřednictvím rozšíření VSPackages stránky možností, měli byste přidat i podporu automatizace. Další informace najdete v tématu [podporu automatizace pro stránky možnosti](../../extensibility/internals/automation-support-for-options-pages.md).  
  
## <a name="standard-automation-objects"></a>Objekty standardní automatizace  
 Rozšíření automatizace pro projekty, také implementovat objekty standardní automatizace (odvozený od `IDispatch`), který odlišit se vedle dalších objektů projektu a implementujte standardní metody a vlastnosti. Standardní objekty příklady projektu objekty, které jsou vloženy do hierarchii řešení, jako například `Projects`, `Project`, `ProjectItem`, a `ProjectItems`. Každý nový typ projektu by měly implementovat tyto objekty (a případně i další značky v závislosti na sémantiku projektu).  
  
 V tom smyslu tyto objekty poskytují opačné výhod VSPackage specifické objekty projektu. Standardní automatizační objekty umožňují projekt tak, aby se použije v zobecněné způsob stejně jako libovolný jiný projekt podporuje stejné objekty. Díky tomu se doplněk, která je napsána proti Obecné `Project` a `ProjectItem` objekty, které můžou fungovat s projekty libovolného typu. Další informace najdete v tématu [projektu modelování](../../extensibility/internals/project-modeling.md).

