---
title: 'Návrhář postupu provádění-postupy: přidání aktivit do sady nástrojů'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b3a8a785-5928-457a-8a50-30267e29503d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d3cde4f3a41a1a07f982f85c0c19e9f16b047068
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593925"
---
# <a name="how-to-add-activities-to-the-toolbox"></a>Postupy: přidání aktivit do sady nástrojů

Aktivity lze do **sady nástrojů** ve vašem řešení přidat několika různými způsoby. Můžete je přidat v rámci aktuálního projektu, odkazovat na ně z jiného projektu nebo na ně odkazovat z jiného sestavení.

## <a name="to-add-an-activity-from-within-your-current-project"></a>Přidání aktivity v rámci aktuálního projektu

1. Přidejte novou vlastní aktivitu do projektu aktuálního pracovního postupu. Další informace o přidání nové vlastní aktivity do projektu naleznete v tématu [How to: Add a New Item to a Project Workflow](../workflow-designer/how-to-add-a-new-item-to-a-workflow-project.md).

2. Přidejte k aktivitě vlastní logiku.

3. Sestavte projekt. Pokud bylo sestavení úspěšné, zobrazí se nová kategorie v **sadě nástrojů** s názvem "\<*projektu název*>" s vlastní aktivitou zahrnutou v této kategorii.

    > [!NOTE]
    > Pokud je sada nástrojů resetována, vlastní aktivity budou odebrány i v případě, že je řešení znovu vytvořeno. Chcete-li znovu naplnit sadu nástrojů vlastními aktivitami po obnovení, restartujte aplikaci Visual Studio.

    > [!NOTE]
    > Sada nástrojů může zobrazit pouze jednu aktivitu daného názvu. Pokud mají dvě aktivity z různých sestavení stejný název třídy, zobrazí se pouze jedna.

    > [!NOTE]
    > Doména aplikace je sdílena mezi instancemi editoru; Pokud jsou použity statické proměnné, budou sdíleny i mezi instancemi editoru. Pokud se nejedná o požadované chování, je třeba použít službu ke sledování instancí proměnných. Informace o používání služeb v Návrháři najdete v tématu [použití kontextu úprav ModelItem](/dotnet/framework/windows-workflow-foundation/using-the-modelitem-editing-context) .

## <a name="to-add-an-activity-from-within-a-different-project"></a>Přidání aktivity v rámci jiného projektu

1. Otevřete řešení, které obsahuje alespoň jeden projekt pracovního postupu, a buď vlastní projekt knihovny aktivit, nebo jiný projekt pracovního postupu, který definuje vlastní aktivitu.

2. Sestavujte oba projekty. Pokud byla sestavení úspěšná, zobrazí se nová kategorie v **sadě nástrojů** s názvem "\<*projektu název*>" s vlastní aktivitou zahrnutou v této kategorii.

## <a name="to-add-an-activity-to-the-toolbox-from-an-assembly"></a>Přidání aktivity do sady nástrojů ze sestavení

1. Otevřete řešení pracovního postupu.

2. V nabídce **nástroje** vyberte **možnost zvolit položky sady nástrojů**.

3. V dialogovém okně **zvolit položky sady nástrojů** vyberte kartu **komponenty System. Activities** a potom klikněte na tlačítko **Procházet** a přejděte do sestavení, které obsahuje vlastní aktivitu, kterou chcete přidat.

4. Vyberte sestavení a klikněte na **OK**. Vlastní komponenta aktivity se přidá do seznamu součástí a automaticky se vybere.

    1. Kliknutím na tlačítko **OK** zavřete dialogové okno.

5. Chcete-li zobrazit sadu nástrojů, vyberte v nabídce **zobrazení** možnost **Sada nástrojů** .

6. Vlastní aktivita se zobrazí v **sadě nástrojů** pod kategorií, která byla před přidáním položky aktivní. Pokud byla například v **sadě nástrojů** vybrána kategorie **Obecné** před přidáním položky sady nástrojů, aktivita se zobrazí v kategorii **Obecné** .

## <a name="see-also"></a>Viz také:

- [Používání návrháře postupu provádění](developing-applications-with-the-workflow-designer.md)
