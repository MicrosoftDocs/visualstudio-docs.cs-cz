---
title: Přidání aktivit do panelu nástrojů
description: V Návrhář postupu provádění se naučíte přidávat aktivity do sady nástrojů ve vašem řešení jejich přidáním z aktuálního projektu nebo jejich odkazování z jiného projektu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: b3a8a785-5928-457a-8a50-30267e29503d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0f2ffdb25bfdb359352d62913c984cad07c18aed
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996302"
---
# <a name="how-to-add-activities-to-the-toolbox"></a>Postupy: Přidání aktivit do panelu nástrojů

Aktivity lze do **sady nástrojů** ve vašem řešení přidat několika různými způsoby. Můžete je přidat v rámci aktuálního projektu, odkazovat na ně z jiného projektu nebo na ně odkazovat z jiného sestavení.

## <a name="to-add-an-activity-from-within-your-current-project"></a>Přidání aktivity v rámci aktuálního projektu

1. Přidejte novou vlastní aktivitu do projektu aktuálního pracovního postupu. Další informace o přidání nové vlastní aktivity do projektu naleznete v tématu [How to: Add a New Item to a Project Workflow](../workflow-designer/how-to-add-a-new-item-to-a-workflow-project.md).

2. Přidejte k aktivitě vlastní logiku.

3. Sestavte projekt. Pokud bylo sestavení úspěšné, zobrazí se nová kategorie v **sadě nástrojů** s názvem " \<*project name*> " s vlastní aktivitou zahrnutou v této kategorii.

    > [!NOTE]
    > Pokud je sada nástrojů resetována, vlastní aktivity budou odebrány i v případě, že je řešení znovu vytvořeno. Chcete-li znovu naplnit sadu nástrojů vlastními aktivitami po obnovení, restartujte aplikaci Visual Studio.

    > [!NOTE]
    > Sada nástrojů může zobrazit pouze jednu aktivitu daného názvu. Pokud mají dvě aktivity z různých sestavení stejný název třídy, zobrazí se pouze jedna.

    > [!NOTE]
    > Doména aplikace je sdílena mezi instancemi editoru; Pokud jsou použity statické proměnné, budou sdíleny i mezi instancemi editoru. Pokud se nejedná o požadované chování, je třeba použít službu ke sledování instancí proměnných. Informace o používání služeb v Návrháři najdete v tématu [použití kontextu úprav ModelItem](/dotnet/framework/windows-workflow-foundation/using-the-modelitem-editing-context) .

## <a name="to-add-an-activity-from-within-a-different-project"></a>Přidání aktivity v rámci jiného projektu

1. Otevřete řešení, které obsahuje alespoň jeden projekt pracovního postupu, a buď vlastní projekt knihovny aktivit, nebo jiný projekt pracovního postupu, který definuje vlastní aktivitu.

2. Sestavujte oba projekty. Pokud byla sestavení úspěšná, zobrazí se nová kategorie v **sadě nástrojů** s názvem " \<*project name*> " s vlastní aktivitou zahrnutou v této kategorii.

## <a name="to-add-an-activity-to-the-toolbox-from-an-assembly"></a>Přidání aktivity do sady nástrojů ze sestavení

1. Otevřete řešení pracovního postupu.

2. V nabídce **nástroje** vyberte **možnost zvolit položky sady nástrojů**.

3. V dialogovém okně **zvolit položky sady nástrojů** vyberte kartu **komponenty System. Activities** a potom klikněte na tlačítko **Procházet** a přejděte do sestavení, které obsahuje vlastní aktivitu, kterou chcete přidat.

4. Vyberte sestavení a klikněte na **OK**. Vlastní komponenta aktivity se přidá do seznamu součástí a automaticky se vybere.

    1. Kliknutím na tlačítko **OK** zavřete dialogové okno.

5. Chcete-li zobrazit sadu nástrojů, vyberte v nabídce **zobrazení** možnost **Sada nástrojů** .

6. Vlastní aktivita se zobrazí v **sadě nástrojů** pod kategorií, která byla před přidáním položky aktivní. Pokud byla například v **sadě nástrojů** vybrána kategorie **Obecné** před přidáním položky sady nástrojů, aktivita se zobrazí v kategorii **Obecné** .

## <a name="see-also"></a>Viz také

- [Použití návrháře postupu provádění](developing-applications-with-the-workflow-designer.md)
