---
title: Zjednodušené vkládání | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - simple view embedding
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b9bc9619ae1ed75aed3656ff014296f7c7d88fa0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700077"
---
# <a name="simplified-embedding"></a>Zjednodušená vkládání
Zjednodušené vkládání je povoleno v editoru, když je jeho objekt zobrazení dokumentu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]nadřazený (tj. zhotoveno podřízené) a <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> rozhraní je implementováno pro zpracování jeho příkazů okna. Zjednodušené editory vkládání nemohou hostovat aktivní ovládací prvky. Objekty použité k vytvoření editoru se zjednodušeným vkládáním jsou znázorněny na následujícím obrázku.

 ![Zjednodušená grafika editoru vkládání](../extensibility/media/vssimplifiedembeddingeditor.gif "vsSimplifiedEmbeddingEditor") Editor se zjednodušeným vkládáním

> [!NOTE]
> Z objektů na tomto obrázku je k vytvoření standardního `CYourEditorFactory` editoru založeného na souborech vyžadován pouze objekt. Pokud vytváříte vlastní editor, není nutné <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>implementovat , protože editor bude pravděpodobně mít vlastní mechanismus trvalosti soukromé. Pro nevlastní editory však musíte tak učinit.

 Všechna rozhraní implementovaná k vytvoření editoru se zjednodušeným vkládáním jsou obsažena v objektu. `CYourEditorDocument` Chcete-li však podporovat více zobrazení dat dokumentu, rozdělte rozhraní na samostatná data a zobrazte objekty, jak je uvedeno v následující tabulce.

|Rozhraní|Umístění rozhraní|Použití|
|---------------|---------------------------|---------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Zobrazit|Poskytuje připojení k nadřazenému oknu.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Zobrazit|Zpracovává příkazy.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Zobrazit|Povolí aktualizace stavového řádku.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Zobrazit|Povolí položky **panelu nástrojů.**|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|Data|Odešle oznámení při změně souboru.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Data|Povolí funkci Uložit jako pro typ souboru.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|Data|Povolí trvalost dokumentu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|Data|Umožňuje potlačení událostí změny souboru, jako je například opětovné spuštění načtení.|
