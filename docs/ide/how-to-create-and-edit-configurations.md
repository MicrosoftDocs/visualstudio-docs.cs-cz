---
title: 'Postup: Vytváření a úpravy konfigurací'
ms.date: 06/21/2017
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- solution build configurations, editing
- build configurations, creating
- solution build configurations, creating
- build configurations, editing
- builds [Visual Studio], setting up
- property pages
- Configuration Manager
- project build configurations, creating
- project build configurations, editing
ms.assetid: 19be121c-148e-4ece-bbfc-d20b08cfc3f7
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 754d2ceef776ab0dea2d8d51151d4170839173b9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114696"
---
# <a name="how-to-create-and-edit-configurations"></a>Postup: Vytváření a úpravy konfigurací

Můžete vytvořit několik konfigurací sestavení pro řešení. Můžete například nakonfigurovat sestavení ladění, které mohou testeři použít k vyhledání a opravě problémů, a můžete nakonfigurovat různé druhy sestavení, které můžete distribuovat různým zákazníkům.

> [!NOTE]
> Toto téma platí pro Visual Studio v systému Windows. Visual Studio pro Mac najdete v [tématu Vytváření a úpravy konfigurací ve Visual Studiu for Mac](/visualstudio/mac/create-and-edit-configurations).

## <a name="create-build-configurations"></a>Vytvoření konfigurací sestavení

Pomocí dialogového okna **Správce konfigurace** můžete vybrat nebo upravit existující konfigurace sestavení nebo vytvořit nové.

Chcete-li otevřít dialogové okno **Správce konfigurace,** otevřete v **Průzkumníku řešení**místní nabídku řešení a pak zvolte **Configuration Manager**.

> [!NOTE]
> Pokud se příkaz **Configuration Manager** v místní nabídce nezobrazí, podívejte se do nabídky **Sestavení** na řádku nabídek. Pokud se tam také nezobrazuje, na řádku nabídek zvolte**General** **Možnosti nástrojů** > **Options**a potom v levém podokně dialogového okna **Možnosti** rozbalte **položku Projekty a obecně řešení** > a v pravém podokně zaškrtněte políčko **Zobrazit upřesňující konfigurace sestavení.**

V dialogovém okně **Nástroj pro nástroj Configuration Manager** můžete pomocí rozevíracího seznamu Konfigurace **aktivního řešení** vybrat konfiguraci sestavení pro celé řešení, upravit existující konfiguraci nebo vytvořit novou konfiguraci. Pomocí rozevíracího seznamu **Aktivní platforma řešení** můžete vybrat platformu, na kterou se konfigurační cílí, upravit existující platformu nebo přidat novou platformu. Podokno **Kontexty projektu** uvádí projekty v řešení. Pro každý projekt můžete vybrat konfiguraci a platformu specifickou pro projekt, upravit stávající nebo vytvořit novou konfiguraci nebo přidat novou platformu. Můžete také zaškrtnout políčka, která označují, zda každý projekt je zahrnuta při použití konfigurace celého řešení k sestavení nebo nasazení řešení.

Po nastavení požadovaných konfigurací můžete nastavit vlastnosti projektu, které jsou vhodné pro tyto konfigurace.

### <a name="set-properties-based-on-configurations"></a>Nastavení vlastností na základě konfigurací

Chcete-li nastavit vlastnosti na základě konfigurací, otevřete v **Průzkumníku řešení**místní nabídku projektu a pak zvolte **Vlastnosti**. Můžete nastavit vlastnosti pro konfigurace. Například pro konfiguraci vydání můžete určit, že kód je optimalizován při sestavení řešení a pro `DEBUG` konfiguraci ladění můžete určit, že symbol podmíněné kompilace je zahrnut.

Další informace o nastavení stránky vlastností naleznete v [tématu Správa vlastností projektu a řešení](../ide/managing-project-and-solution-properties.md).

## <a name="create-a-project-configuration"></a>Vytvoření konfigurace projektu

1. Otevřete dialogové okno **Správce konfigurace.**

2. Vyberte projekt ve sloupci **Projekt.**

3. V rozevíracím seznamu **Konfigurace** pro tento projekt zvolte **Nový**.

     Otevře se dialogové okno **Nová konfigurace projektu.**

4. Do pole **Název** zadejte název nové konfigurace.

5. Chcete-li použít nastavení vlastností z existující konfigurace projektu, zvolte v rozevíracím seznamu **Nastavení kopírování z** rozbalovacího seznamu.

6. Chcete-li současně vytvořit konfiguraci pro celé řešení, zaškrtněte políčko **Vytvořit novou konfiguraci řešení.**

## <a name="rename-a-project-configuration"></a>Přejmenování konfigurace projektu

1. Otevřete dialogové okno **Správce konfigurace.**

2. Ve sloupci **Projekt** vyberte projekt, který má konfiguraci projektu, kterou chcete přejmenovat.

3. V rozevíracím seznamu **Konfigurace** pro tento projekt zvolte **Upravit**.

     Otevře se dialogové okno **Upravit konfigurace projektu.**

4. Vyberte název konfigurace projektu, který chcete změnit.

5. Vyberte **Přejmenovat**a zadejte nový název.

## <a name="create-and-modify-solution-wide-build-configurations"></a>Vytváření a úpravy konfigurací sestavení pro celé řešení

### <a name="to-create-a-solution-wide-build-configuration"></a>Vytvoření konfigurace sestavení pro celé řešení

1. Otevřete dialogové okno **Správce konfigurace.**

2. V rozevíracím seznamu **Konfigurace aktivního řešení** zvolte **Nový**.

     Otevře se dialogové okno **Nová konfigurace řešení.**

3. Do textového pole **Název** zadejte název nové konfigurace.

4. Chcete-li použít nastavení z existující konfigurace řešení, zvolte v rozevíracím seznamu **Nastavení kopírování z** rozbalovacího seznamu.

5. Pokud chcete vytvořit konfigurace projektu současně, zaškrtněte políčko **Vytvořit nové konfigurace projektu.**

### <a name="to-rename-a-solution-wide-build-configuration"></a>Přejmenování konfigurace sestavení pro celé řešení

1. Otevřete dialogové okno **Správce konfigurace.**

2. V rozevíracím seznamu **Konfigurace aktivního řešení** zvolte **Upravit**.

     Otevře se dialogové okno **Upravit konfigurace řešení.**

3. Vyberte název konfigurace řešení, který chcete změnit.

4. Vyberte **Přejmenovat**a zadejte nový název.

### <a name="to-modify-a-solution-wide-build-configuration"></a>Úprava konfigurace sestavení pro celé řešení

1. Otevřete dialogové okno **Správce konfigurace.**

2. V rozevíracím seznamu **Konfigurace aktivního řešení** vyberte požadovanou konfiguraci.

3. V podokně **Kontexty projektu** pro každý projekt vyberte **požadovanou konfiguraci** a **platformu** a vyberte, zda se má **sestavit** a zda se má **nasadit.**

## <a name="see-also"></a>Viz také

- [Vysvětlení konfigurací sestavení](../ide/understanding-build-configurations.md)
- [Vytváření a čištění projektů a řešení v sadě Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Správa vlastností projektu a řešení](managing-project-and-solution-properties.md)
- [Vytváření a úpravy konfigurací (Visual Studio pro Mac)](/visualstudio/mac/create-and-edit-configurations)
