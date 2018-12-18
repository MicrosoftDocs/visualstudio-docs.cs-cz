---
title: 'Návrhář postupu provádění - postupy: přidání aktivit do sady nástrojů'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: b3a8a785-5928-457a-8a50-30267e29503d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a009f36152163e3ac23b85deac4ea99f26092be9
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37118210"
---
# <a name="how-to-add-activities-to-the-toolbox"></a>Postupy: přidání aktivit do sady nástrojů

Aktivity mohou být přidány do **sada nástrojů** ve vašem řešení v několika různými způsoby. Můžete přidat z aktuálního projektu, na ně odkazovat z jiného projektu nebo na ně odkazovat z jiného sestavení.

## <a name="to-add-an-activity-from-within-your-current-project"></a>Chcete-li přidat aktivitu z v aktuálním projektu

1.  Přidejte novou vlastní aktivitu do aktuálního projektu pracovního postupu. Další informace o přidání nové vlastní aktivity do projektu najdete v tématu [postupy: Přidat novou položku do projektu Workflow](../workflow-designer/how-to-add-a-new-item-to-a-workflow-project.md).

2.  Přidáte vlastní logiky do vaši aktivitu.

3.  Sestavte projekt. Pokud bylo úspěšné, sestavení novou kategorii v **sada nástrojů** s názvem "\<*název projektu*>" se zobrazí s vlastní aktivity, které jsou součástí této kategorie spadají.

    > [!NOTE]
    > Pokud se resetuje sady nástrojů, vlastní aktivity se odebere, i v případě, že je řešení znovu sestaven. Znovu naplnit nástrojů vlastní aktivity po byla obnovena, restartujte Visual Studio.

    > [!NOTE]
    > V panelu nástrojů můžete zobrazit pouze jednu aktivitu daného názvu. Pokud dvě aktivity z různých sestavení mají stejný název třídy, se zobrazí pouze jeden.

    > [!NOTE]
    > Doména aplikace je sdílen mezi editor instance; Pokud se používají statické proměnné, bude sdílena mezi také instance editoru. Pokud není toto chování žádoucí, služby slouží ke sledování proměnné instancí. V tématu [pomocí kontextu úpravy typem ModelItem](/dotnet/framework/windows-workflow-foundation/using-the-modelitem-editing-context) informace o používání služby v návrháři.

## <a name="to-add-an-activity-from-within-a-different-project"></a>Chcete-li přidat aktivitu z v rámci jiného projektu

1.  Otevřete řešení, které obsahuje alespoň jeden pracovní postup projekt a projekt knihovny vlastní aktivity nebo jiného projektu pracovního postupu, který definuje vlastní aktivity.

2.  Sestavení obou projektů. Pokud sestavení, které byly úspěšné, novou kategorii v **sada nástrojů** s názvem "\<*název projektu*>" se zobrazí s vlastní aktivity, které jsou součástí této kategorie spadají.

## <a name="to-add-an-activity-to-the-toolbox-from-an-assembly"></a>Chcete-li přidat aktivity do sady nástrojů ze sestavení

1.  Otevřete řešení pracovního postupu.

2.  Z **nástroje** nabídce vyberte možnost **výběr položek sady nástrojů**.

3.  V **výběr položek sady nástrojů** dialogové okno, vyberte **systém. součásti** kartě a pak klikněte na **Procházet** přejděte na sestavení, které obsahuje vlastní aktivity, které chcete přidat.

4.  Vyberte sestavení a klikněte na **OK**. Součást vlastní aktivity se přidá do seznamu součástí a je automaticky vybrán.

    1.  Klikněte na tlačítko **OK** zavřete dialogové okno.

5.  Pokud chcete zobrazit sady nástrojů, vyberte **sada nástrojů** z **zobrazení** nabídky.

6.  Vlastní aktivity se zobrazí v **sada nástrojů** v kategorii, která byla aktivní před přidáním položky. Například pokud **Obecné** kategorie byla vybrána v **sada nástrojů** před přidáním položky panelu nástrojů, tato aktivita se zobrazí v části **Obecné** kategorie.

## <a name="see-also"></a>Viz také:

- [Používání návrháře postupu provádění](../workflow-designer/using-the-workflow-designer.md)