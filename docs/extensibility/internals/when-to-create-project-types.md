---
title: Kdy vytvořit typy projektů | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, conditions for creating
ms.assetid: 26adc860-ee4a-4f5c-95e1-e41b207dd7e6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 861250dac25288f353cbd5c57f510bf67dadce70
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703434"
---
# <a name="when-to-create-project-types"></a>Kdy vytvořit typy projektů
Vytvoření nového typu projektu poskytuje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] základ pro přizpůsobení pro uživatele. Vytvoření nového typu projektu však [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] není vyžadováno pro všechna vlastní nastavení. Následující pokyny by vám měly pomoci určit, zda je pro váš scénář vyžadován nový typ projektu.

## <a name="create-a-new-project-type"></a>Vytvoření nového typu projektu
 Typ projektu je nutné vytvořit, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pokud chcete přizpůsobit tak, aby jednaljedním nebo více z následujících způsobů:

- Zapojte se do sestavení, nasazení, konfigurace a správy zdrojového kódu.

- Nabídněte podporu ladění.

- Zobrazení položek projektu v **Průzkumníku řešení**.

- Použijte dialogové okno **Otevřít projekt** nebo **Nový projekt.**

- Podpora vnoření projektu.

## <a name="extend-an-existing-project-type"></a>Rozšíření existujícího typu projektu
 Můžete chtít vytvořit nový typ projektu, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] který lze použít následujícími způsoby k úpravě nebo rozšíření chování existujícího typu projektu, například úpravou procesu sestavení pro [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projekty:

- Pracujte s více soubory jako s jednou jednotkou.

- Zobrazí jeden soubor jako hierarchii dílčích položek.

- Zobrazení kontextu příkazu kolem editorů.

- Zobrazení kontextu služby pro editory.

## <a name="use-an-existing-project-type"></a>Použití existujícího typu projektu
 Vytvoření nového projektu někdy není nutné. V následující tabulce jsou uvedeny úkoly, pro které není třeba vytvářet typ projektu.

|Úkol|Popis|
|----------|-----------------|
|Zpracování příkazů|Všechny příkazy VSPackage mohou zpracovávat.|
|Vytvoření editoru|Vlastní editory mohou být registrovány. Další informace naleznete [v tématu Document Windows and Editors](https://msdn.microsoft.com/library/603625e1-62b6-413a-bc44-089346e166bc).|
|Vlastnictví oken|Okna nástrojů i dokumentů můžete vytvořit bez přidání nového typu projektu.|
|Vystavení vlastností v okně Vlastnosti|Všechny objekty mohou vystavit vlastnosti.|

## <a name="create-a-project-subtype"></a>Vytvoření podtypu projektu
 Podtypy projektu můžete použít k rozšíření spravovaného typu projektu bez nutnosti vytvářet nový typ projektu. Podtypy projektu používají agregaci COM k [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] rozšíření [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]spravovaných projektů napsaných v microsoftu nebo . Pomocí agregace COM můžete znovu použít velkou část implementace spravovaného systému projektu a stále přizpůsobit pro konkrétní scénář prostřednictvím agregace a použití podpůrných rozhraní. Další informace o podtypech projektů naleznete v [tématu Podtypy projektu](../../extensibility/internals/project-subtypes.md).

## <a name="see-also"></a>Viz také
- [Dokument windows a editory](https://msdn.microsoft.com/library/603625e1-62b6-413a-bc44-089346e166bc)
- [Kontrolní seznam: Vytvoření nových typů projektů](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Hierarchie v sadě Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)
