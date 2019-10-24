---
title: Kdy vytvořit typy projektů | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, conditions for creating
ms.assetid: 26adc860-ee4a-4f5c-95e1-e41b207dd7e6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff29843965c220c505266a9cd973e5695c0b9dab
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721556"
---
# <a name="when-to-create-project-types"></a>Kdy vytvořit typy projektů
Vytvořením nového typu projektu získáte základ pro přizpůsobení [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pro vaše uživatele. Vytvoření nového typu projektu však není vyžadováno pro všechna [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] přizpůsobení. Následující pokyny vám pomohou určit, zda je pro váš scénář požadován nový typ projektu.

## <a name="create-a-new-project-type"></a>Vytvořit nový typ projektu
 Typ projektu musíte vytvořit, pokud chcete přizpůsobit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], aby fungovala v jednom nebo několika následujících způsobech:

- Zapojit se do sestavení, nasazení, konfigurací a správy zdrojového kódu.

- Nabízí podporu ladění.

- Zobrazit položky projektu v **Průzkumník řešení**.

- Použijte dialogové okno **Otevřít projekt** nebo **Nový projekt** .

- Podporuje vnořování projektů.

## <a name="extend-an-existing-project-type"></a>Rozšíří existující typ projektu
 Můžete chtít vytvořit nový typ projektu, který lze použít [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] následujícími způsoby, jak upravit nebo zvětšit chování existujícího typu projektu, například úpravou procesu sestavení pro [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projekty:

- Pracujte s více soubory jako s jednou jednotkou.

- Zobrazí jeden soubor jako hierarchii dílčích položek.

- Zobrazí kontext příkazu kolem editorů.

- Zobrazit kontext služby pro editory.

## <a name="use-an-existing-project-type"></a>Použít existující typ projektu
 Vytvoření nového projektu někdy není nutné. V následující tabulce jsou uvedeny úlohy, které nemusíte vytvořit typ projektu pro.

|Úloha|Popis|
|----------|-----------------|
|Zpracování příkazů|Všechny VSPackage můžou zpracovávat příkazy.|
|Sestavování editoru|Vlastní editory je možné zaregistrovat. Další informace najdete v tématu [okna a editory dokumentů](https://msdn.microsoft.com/library/603625e1-62b6-413a-bc44-089346e166bc).|
|Vlastnící okna|Můžete vytvořit okna nástrojů i dokumentu bez přidání nového typu projektu.|
|Vystavení vlastností v okno Vlastnosti|Všechny objekty mohou vystavit vlastnosti.|

## <a name="create-a-project-subtype"></a>Vytvoření podtypu projektu
 Můžete použít podtypy projektu pro rozšiřování spravovaného typu projektu bez nutnosti vytvořit nový typ projektu. Podtypy projektů používají agregaci COM k rozšiřování spravovaných projektů napsaných v Microsoft [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] nebo [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]. Pomocí agregace modelu COM můžete znovu použít většinu implementace spravovaného projektového systému a ještě přizpůsobit konkrétní scénář prostřednictvím agregace a používání podpůrných rozhraní. Další informace o podtypůch projektů naleznete v tématu [podtypy projektu](../../extensibility/internals/project-subtypes.md).

## <a name="see-also"></a>Viz také:
- [Okna a editory dokumentů](https://msdn.microsoft.com/library/603625e1-62b6-413a-bc44-089346e166bc)
- [Kontrolní seznam: Vytvoření nových typů projektů](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Hierarchie v sadě Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)