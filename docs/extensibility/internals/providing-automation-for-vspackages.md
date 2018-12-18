---
title: Poskytnutí automatizace pro VSPackages | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, automation [Visual Studio SDK]
- automation [Visual Studio SDK], VSPackages
ms.assetid: 104c4c55-78b8-42f4-b6b0-9a334101aaea
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fb5f3393443e41c9bd99a8890b53bedae006d7a5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131569"
---
# <a name="providing-automation-for-vspackages"></a>Poskytnutí automatizace pro VSPackages
Existují dva hlavní způsoby zajistit automatizace pro vaše VSPackages: implementací VSPackage konkrétní objekty a implementací objekty standardní automatizace. Obecně platí ty se používají společně rozšířit model automatizace prostředí.  
  
## <a name="vspackage-specific-objects"></a>VSPackage specifické objekty  
 Určitých místech v rámci modelu automatizace musíte poskytnout objekty automatizace, které jsou jedinečné pro vaše VSPackage. Například nové projekty vyžadují odlišné objekty, které poskytuje jenom vaše VSPackage. Názvy těchto objektů jsou uloženy do registru a získat prostřednictvím volání do prostředí `DTE` objektu.  
  
 VSPackage specifické objekty můžete získat také při příjemce automatizace používá objekt poskytnutý prostřednictvím vlastnosti objektu standardní objektu. Například standardní `Window` objekt má `Object` vlastnosti, které se běžně označuje jako `Windows.Object` vlastnost. Když uživatelé volat `Window.Object` na okno implementované v vaší VSPackage, předáte zpět objekt konkrétní automatizace vlastní návrh.  
  
#### <a name="projects"></a>Projekty  
 VSPackages můžete rozšířit model automatizace pro nové typy projektů prostřednictvím svých vlastních VSPackage konkrétní objekty. Primárním účelem poskytnutí nové objekty automatizace pro vaše VSPackage je k odlišení projektu jedinečný objekty od <xref:Microsoft.VisualStudio.VCProjectEngine.VCProject> nebo <xref:VSLangProj80.VSProject2> objektu. Tento rozdíl je užitečný, pokud chcete poskytnout způsob, jak vyčlenit nebo iteraci typ vašeho projektu kromě jiných typů projektů má zobrazit vedle sebe v řešení. Další informace najdete v tématu [vystavení objektů projektu](../../extensibility/internals/exposing-project-objects.md).  
  
#### <a name="events"></a>Události  
 Architektura událostí prostředí nabízí jiné místo abyste připojit vlastní VSPackage konkrétní objekty. Například tak, že vytvoříte vlastní objekty jedinečný událostí, můžete rozšířit model událostí v prostředí pro projekty. Můžete chtít zadat vlastní události při přidání nové položky do vlastního typu projektu. Další informace najdete v tématu [vystavení události](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md).  
  
#### <a name="window-objects"></a>Objekty oken  
 Windows můžete předat zpět objekt automatizace VSPackage konkrétní zpět do prostředí při volání. Implementace objektu, který je odvozený od <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>, <xref:EnvDTE.IExtensibleObject> nebo `IDispatch` , předá zpět vlastnosti, rozšíření objektu okna, ve kterém je umístěný. Například můžete použít tento přístup zajistit automatizace pro ovládací prvek umístěný v rámce okna. Sémantika tento objekt a všechny další objekty, které může prodloužit je váš návrh. Další informace najdete v tématu [postupy: poskytování automatizaci pro systém Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md).  
  
#### <a name="options-pages-on-the-tools-menu"></a>Možnosti stránky v nabídce Nástroje  
 Můžete vytvořit stránky rozšířit nástroje, Možnosti automatizace modelu prostřednictvím implementace stránky a přidání informací do registru a vytvořit vlastní možnosti. Vaše stránky může být volána prostřednictvím modelu objektu prostředí jako ostatní možnosti stránky. Pokud návrh funkce, kterou chcete přidat do prostředí prostřednictvím VSPackages vyžaduje možnosti stránky, měli byste přidat také podpora automatizace. Další informace najdete v tématu [automatizace podporu pro možnosti stránky](../../extensibility/internals/automation-support-for-options-pages.md).  
  
## <a name="standard-automation-objects"></a>Objekty standardní automatizace  
 Rozšířit automatizace pro projekty, můžete taky implementovat objekty standardní automatizace (odvozený z `IDispatch`), stát vedle jiné objekty projektu a implementovat standardní metody a vlastnosti. Standardní objektů projektu objekty, které jsou vloženy do hierarchie řešení, jako příklady `Projects`, `Project`, `ProjectItem`, a `ProjectItems`. Každý nový projekt typ měli implementovat tyto objekty (a případně dalších ty, které jsou v závislosti na sémantiky projektu).  
  
 V tom smyslu zadejte tyto objekty opačné výhod VSPackage specifické objekty projektu. Objekty standardní automatizace povolit projektu, který se má použít zobecněný způsobem, jako je podpora stejné objekty jiných projektů. Proto doplněk, který je napsaných pro obecné `Project` a `ProjectItem` objekty může pracovat s projekty libovolného typu. Další informace najdete v tématu [projekt modelování](../../extensibility/internals/project-modeling.md).