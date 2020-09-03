---
title: Poskytování automatizace pro VSPackage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, automation [Visual Studio SDK]
- automation [Visual Studio SDK], VSPackages
ms.assetid: 104c4c55-78b8-42f4-b6b0-9a334101aaea
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6364f9cbaf3409e076eeb77365e5d793c7be96cb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80705951"
---
# <a name="providing-automation-for-vspackages"></a>Poskytování automatizace pro balíčky VSPackages
Existují dva hlavní způsoby, jak zajistit automatizaci pro sady VSPackage: implementace objektů specifických pro VSPackage a implementace standardních objektů automatizace. Obecně se používají společně k rozšiřování modelu automatizace prostředí.

## <a name="vspackage-specific-objects"></a>Objekty specifické pro VSPackage
 Určitá místa v modelu automatizace vyžadují, abyste poskytovali automatizační objekty, které jsou pro VSPackage jedinečné. Například nové projekty vyžadují odlišné objekty, které poskytuje pouze vaše VSPackage. Názvy těchto objektů jsou zadány v registru a získány prostřednictvím volání do `DTE` objektu prostředí.

 Objekty specifické pro VSPackage lze také získat, pokud uživatel automatizace používá objekt poskytnutý prostřednictvím vlastnosti Object standardního objektu. Například standardní `Window` objekt má `Object` vlastnost, která se často označuje jako `Windows.Object` vlastnost. Když spotřebitelé volají v `Window.Object` okně implementovaném ve VSPackage, předáte zpět konkrétní automatizační objekt vlastního návrhu.

#### <a name="projects"></a>Projekty
 Sady VSPackage mohou roztáhnout model automatizace pro nové typy projektů prostřednictvím jejich vlastních objektů pro rozhraní VSPackage. Hlavním účelem poskytování nových automatizačních objektů pro VSPackage je odlišit vaše jedinečné objekty projektu od <xref:Microsoft.VisualStudio.VCProjectEngine.VCProject> <xref:VSLangProj80.VSProject2> objektu nebo. Tato odlišnost je užitečná, pokud chcete poskytnout způsob, jak vycházet z jiných typů projektů nebo iterovat typ projektu, by se měl zobrazit vedle sebe v řešení. Další informace naleznete v tématu vystavení [objektů projektu](../../extensibility/internals/exposing-project-objects.md).

#### <a name="events"></a>Události
 Architektura událostí prostředí nabízí další místo, kde můžete připojit vlastní objekty specifické pro VSPackage. Například vytvořením vlastních jedinečných objektů událostí můžete roztáhnout model událostí prostředí pro projekty. Můžete chtít poskytnout vlastní události, když je přidána nová položka do vlastního typu projektu. Další informace najdete v tématu vystavení [událostí](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md).

#### <a name="window-objects"></a>Objekty oken
 Systém Windows může při volání předat zpátky objekt Automation specifický pro VSPackage zpátky do prostředí. Implementujete objekt, který je odvozen z <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject> <xref:EnvDTE.IExtensibleObject> nebo `IDispatch` který vrací vlastnosti zpět, rozšíření objektu okna, ve kterém je umístěno. Tento přístup můžete například použít k poskytnutí automatizace pro ovládací prvek, který je součástí rámce okna. Sémantika tohoto objektu a všech dalších objektů, které by mohly být rozšířeny, jsou vaše návrhy. Další informace najdete v tématu [Postup: poskytnutí automatizace pro Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md).

#### <a name="options-pages-on-the-tools-menu"></a>Stránky možností v nabídce nástroje
 Můžete vytvořit stránky pro rozšíření nástrojů, možností modelu automatizace prostřednictvím implementací stránek a přidání informací do registru k vytvoření vlastních možností. Vaše stránky pak mohou být volány prostřednictvím objektového modelu prostředí jako jakékoli jiné stránky možností. Pokud návrh funkce, kterou přidáváte do prostředí prostřednictvím rozhraní VSPackage, vyžaduje stránky možností, měli byste také přidat podporu automatizace. Další informace najdete v tématu [Podpora automatizace pro stránky možností](../../extensibility/internals/automation-support-for-options-pages.md).

## <a name="standard-automation-objects"></a>Standardní automatizační objekty
 Pro rozšiřování automatizace pro projekty implementujete také standardní automatizační objekty (odvozené od `IDispatch` ), které se nacházejí v jiných objektech projektu, a implementujete standardní metody a vlastnosti. Příklady standardních objektů zahrnují objekty projektu, které jsou vloženy do hierarchie řešení, jako například `Projects` , `Project` , `ProjectItem` a `ProjectItems` . Každý nový typ projektu by měl implementovat tyto objekty (a případně i jiné v závislosti na sémantikě projektu).

 Ve smyslu tyto objekty poskytují opačnou výhodu objektů projektu specifických pro VSPackage. Standardní automatizační objekty umožňují, aby byl projekt používán zobecněným způsobem, jako jakýkoliv jiný projekt podporující stejné objekty. Proto doplněk, který je napsán pro obecné `Project` a `ProjectItem` objekty, může fungovat na projektech libovolného typu. Další informace najdete v tématu [modelování projektu](../../extensibility/internals/project-modeling.md).
