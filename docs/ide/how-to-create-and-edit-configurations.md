---
title: 'Postupy: vytváření a úpravy konfigurací'
ms.date: 06/21/2017
ms.technology: vs-ide-compile
ms.topic: how-to
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
ms.openlocfilehash: a5b3ecd4abb05148130b0d87e287cbe199557951
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85284500"
---
# <a name="how-to-create-and-edit-configurations"></a>Postupy: vytváření a úpravy konfigurací

Můžete vytvořit několik konfigurací sestavení pro řešení. Můžete například nakonfigurovat sestavení pro ladění, které můžou testeri použít k vyhledání a opravě problémů, a můžete nakonfigurovat různé druhy sestavení, které můžete distribuovat různým zákazníkům.

> [!NOTE]
> Toto téma se týká sady Visual Studio ve Windows. Visual Studio pro Mac najdete v tématu [Vytvoření a úprava konfigurací v Visual Studio pro Mac](/visualstudio/mac/create-and-edit-configurations).

## <a name="create-build-configurations"></a>Vytvoření konfigurací sestavení

Pomocí dialogového okna **Configuration Manager** můžete vybrat nebo změnit existující konfigurace sestavení nebo vytvořit nové.

Chcete-li otevřít dialogové okno **Configuration Manager** , v **Průzkumník řešení**otevřete místní nabídku řešení a zvolte možnost **Configuration Manager**.

> [!NOTE]
> Pokud se příkaz **Configuration Manager** v místní nabídce nezobrazí, podívejte se do nabídky **sestavení** na řádku nabídek. Pokud se buď nezobrazí, na panelu nabídek zvolte **Tools**  >  **Možnosti**nástroje a pak v levém podokně dialogového okna **Možnosti** rozbalte **projekty a řešení**  >  **Obecné**a v pravém podokně zaškrtněte políčko **Zobrazit pokročilé konfigurace sestavení** .

V dialogovém okně **Configuration Manager** můžete použít rozevírací seznam **Konfigurace aktivního řešení** k výběru konfigurace sestavení pro celé řešení, úpravě existujícího nebo vytvoření nové konfigurace. Pomocí rozevíracího seznamu **Aktivní platforma řešení** můžete vybrat platformu, kterou konfigurace cílí, upravit existující nebo přidat novou platformu. Podokno **kontexty projektu** obsahuje seznam projektů v řešení. Pro každý projekt můžete vybrat konfiguraci a platformu specifickou pro konkrétní projekt, upravit existující nebo vytvořit novou konfiguraci nebo přidat novou platformu. Můžete také zaškrtnout políčka, která určují, zda je každý projekt zahrnut při použití konfigurace pro sestavení nebo nasazení řešení v rámci řešení.

Po nastavení požadovaných konfigurací můžete nastavit vlastnosti projektu, které jsou vhodné pro tyto konfigurace.

### <a name="set-properties-based-on-configurations"></a>Nastavení vlastností na základě konfigurací

Chcete-li nastavit vlastnosti založené na konfiguracích, v **Průzkumník řešení**otevřete místní nabídku pro projekt a poté zvolte možnost **vlastnosti**. Můžete nastavit vlastnosti pro vaše konfigurace. Například pro konfiguraci vydané verze můžete určit, že kód je optimalizován při sestavení řešení a pro konfiguraci ladění, můžete určit, že `DEBUG` je zahrnut symbol podmíněné kompilace.

Další informace o nastavení stránky vlastností naleznete v tématu [Správa vlastností projektu a řešení](../ide/managing-project-and-solution-properties.md).

## <a name="create-a-project-configuration"></a>Vytvoření konfigurace projektu

1. Otevřete dialogové okno **Configuration Manager** .

2. Vyberte projekt ve sloupci **projekt** .

3. V rozevíracím seznamu **Konfigurace** pro daný projekt vyberte možnost **Nový**.

     Otevře se dialogové okno **Nová konfigurace projektu** .

4. Do pole **název** zadejte název nové konfigurace.

5. Chcete-li použít nastavení vlastností z existující konfigurace projektu, v rozevíracím seznamu **Kopírovat nastavení z** vyberte konfiguraci.

6. Chcete-li vytvořit konfiguraci v rámci řešení současně, zaškrtněte políčko **vytvořit novou konfiguraci řešení** .

## <a name="rename-a-project-configuration"></a>Přejmenování konfigurace projektu

1. Otevřete dialogové okno **Configuration Manager** .

2. Ve sloupci **projekt** vyberte projekt s konfigurací projektu, který chcete přejmenovat.

3. V rozevíracím seznamu **Konfigurace** pro daný projekt vyberte možnost **Upravit**.

     Otevře se dialogové okno **Upravit konfigurace projektu** .

4. Vyberte název konfigurace projektu, který chcete změnit.

5. Vyberte **Přejmenovat**a pak zadejte nový název.

## <a name="create-and-modify-solution-wide-build-configurations"></a>Vytváření a úpravy konfigurací sestavení v úrovni řešení

### <a name="to-create-a-solution-wide-build-configuration"></a>Vytvoření konfigurace sestavení na úrovni pro řešení

1. Otevřete dialogové okno **Configuration Manager** .

2. V rozevíracím seznamu **Konfigurace aktivního řešení** vyberte možnost **Nový**.

     Otevře se dialogové okno **Nová konfigurace řešení** .

3. Do textového pole **název** zadejte název nové konfigurace.

4. Chcete-li použít nastavení z existující konfigurace řešení, v rozevíracím seznamu **Kopírovat nastavení z** vyberte konfiguraci.

5. Chcete-li vytvořit konfigurace projektu ve stejnou dobu, zaškrtněte políčko **vytvořit nové konfigurace projektu** .

### <a name="to-rename-a-solution-wide-build-configuration"></a>Přejmenování konfigurace sestavení na úrovni pro řešení

1. Otevřete dialogové okno **Configuration Manager** .

2. V rozevíracím seznamu **Konfigurace aktivního řešení** vyberte možnost **Upravit**.

     Otevře se dialogové okno **Upravit konfigurace řešení** .

3. Vyberte název konfigurace řešení, který chcete změnit.

4. Vyberte **Přejmenovat**a pak zadejte nový název.

### <a name="to-modify-a-solution-wide-build-configuration"></a>Úprava konfigurace sestavení v rámci řešení

1. Otevřete dialogové okno **Configuration Manager** .

2. V rozevíracím seznamu **Konfigurace aktivního řešení** vyberte konfiguraci, kterou chcete.

3. V podokně **kontexty projektu** pro každý projekt vyberte požadovanou **konfiguraci** a **platformu** a vyberte, zda má být **vytvořena** a zda má být **nasazena** .

## <a name="see-also"></a>Viz také

- [Vysvětlení konfigurací sestavení](../ide/understanding-build-configurations.md)
- [Sestavování a čištění projektů a řešení v aplikaci Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Správa vlastností projektu a řešení](managing-project-and-solution-properties.md)
- [Vytvoření a úprava konfigurací (Visual Studio pro Mac)](/visualstudio/mac/create-and-edit-configurations)
