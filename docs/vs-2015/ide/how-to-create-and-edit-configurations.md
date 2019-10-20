---
title: 'Postupy: vytváření a úpravy konfigurací | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d5f5d8bb92b80942a95528a0b2e4c7e64bbfafc8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668145"
---
# <a name="how-to-create-and-edit-configurations"></a>Postupy: Vytvoření a úprava konfigurací
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete vytvořit několik konfigurací sestavení pro řešení. Můžete například nakonfigurovat sestavení pro ladění, které můžou testeri použít k vyhledání a opravě problémů, a můžete nakonfigurovat různé druhy sestavení, které můžete distribuovat různým zákazníkům.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="creating-build-configurations"></a>Vytváření konfigurací sestavení
 Pomocí dialogového okna **Configuration Manager** můžete vybrat nebo změnit existující konfigurace sestavení, nebo můžete vytvořit nové.

#### <a name="to-open-the-configuration-manager-dialog-box"></a>Otevření dialogového okna Configuration Manager

- V **Průzkumník řešení**otevřete místní nabídku řešení a pak zvolte možnost **Configuration Manager**.

  > [!NOTE]
  > Pokud se příkaz **Configuration Manager** v místní nabídce nezobrazí, podívejte se do nabídky **sestavení** na řádku nabídek. Pokud tam buď není, v panelu nabídek zvolte **nástroje**, **Možnosti**a potom v levém podokně dialogového okna **Možnosti** rozbalte **projekty a řešení**, **Obecné**a v pravém podokně vyberte **Zobrazit zaškrtávací políčko Upřesnit konfigurace sestavení** .

   V dialogovém okně **Configuration Manager** můžete použít rozevírací seznam **Konfigurace aktivního řešení** k výběru konfigurace sestavení pro celé řešení, úpravě existujícího nebo vytvoření nové konfigurace. Pomocí rozevíracího seznamu **Aktivní platforma řešení** můžete vybrat platformu, kterou konfigurace cílí, upravit existující nebo přidat novou platformu. Podokno **kontexty projektu** obsahuje seznam projektů v řešení. Pro každý projekt můžete vybrat konfiguraci a platformu specifickou pro konkrétní projekt, upravit existující nebo vytvořit novou konfiguraci nebo přidat novou platformu. Můžete také zaškrtnout políčka, která určují, zda je každý projekt zahrnut při použití konfigurace pro sestavení nebo nasazení řešení v rámci řešení.

  Po nastavení požadovaných konfigurací můžete nastavit vlastnosti projektu, které jsou vhodné pro tyto konfigurace.

#### <a name="to-set-properties-based-on-configurations"></a>Nastavení vlastností na základě konfigurací

- V **Průzkumník řešení**otevřete místní nabídku pro projekt a poté zvolte možnost **vlastnosti**.

     Otevře se okno **stránky vlastností** .

     Můžete nastavit vlastnosti pro vaše konfigurace. Například pro konfiguraci vydání můžete určit, že kód je optimalizován při sestavení řešení a pro konfiguraci ladění, můžete určit, že je zahrnut symbol `DEBUG` podmíněné kompilace. Další informace o nastavení stránky vlastností naleznete v tématu [Úvod do Návrháře projektu](https://msdn.microsoft.com/898dd854-c98d-430c-ba1b-a913ce3c73d7).

## <a name="creating-and-modifying-project-configurations"></a>Vytváření a úpravy konfigurací projektu

#### <a name="to-create-a-project-configuration"></a>Vytvoření konfigurace projektu

1. Otevřete dialogové okno **Configuration Manager** .

2. Vyberte projekt ve sloupci **projekt** .

3. V rozevíracím seznamu **Konfigurace** pro daný projekt vyberte možnost **Nový**.

     Otevře se dialogové okno **Nová konfigurace projektu** .

4. Do pole **název** zadejte název nové konfigurace.

5. Chcete-li použít nastavení vlastností z existující konfigurace projektu, v rozevíracím seznamu **Kopírovat nastavení z** vyberte konfiguraci.

6. Chcete-li vytvořit konfiguraci v rámci řešení současně, zaškrtněte políčko **vytvořit novou konfiguraci řešení** .

#### <a name="to-rename-a-project-configuration"></a>Přejmenování konfigurace projektu

1. Otevřete dialogové okno **Configuration Manager** .

2. Ve sloupci **projekt** vyberte projekt s konfigurací projektu, který chcete přejmenovat.

3. V rozevíracím seznamu **Konfigurace** pro daný projekt vyberte možnost **Upravit**.

     Otevře se dialogové okno **Upravit konfigurace projektu** .

4. Vyberte název konfigurace projektu, který chcete změnit.

5. Vyberte **Přejmenovat**a pak zadejte nový název.

## <a name="creating-and-modifying-solution-wide-build-configurations"></a>Vytváření a úpravy konfigurací sestavení v úrovni řešení

#### <a name="to-create-a-solution-wide-build-configuration"></a>Vytvoření konfigurace sestavení na úrovni pro řešení

1. Otevřete dialogové okno **Configuration Manager** .

2. V rozevíracím seznamu **Konfigurace aktivního řešení** vyberte možnost **Nový**.

     Otevře se dialogové okno **Nová konfigurace řešení** .

3. Do textového pole **název** zadejte název nové konfigurace.

4. Chcete-li použít nastavení z existující konfigurace řešení, v rozevíracím seznamu **Kopírovat nastavení z** vyberte konfiguraci.

5. Chcete-li vytvořit konfigurace projektu ve stejnou dobu, zaškrtněte políčko **vytvořit nové konfigurace projektu** .

#### <a name="to-rename-a-solution-wide-build-configuration"></a>Přejmenování konfigurace sestavení na úrovni pro řešení

1. Otevřete dialogové okno **Configuration Manager** .

2. V rozevíracím seznamu **Konfigurace aktivního řešení** vyberte možnost **Upravit**.

     Otevře se dialogové okno **Upravit konfigurace řešení** .

3. Vyberte název konfigurace řešení, který chcete změnit.

4. Vyberte **Přejmenovat**a pak zadejte nový název.

#### <a name="to-modify-a-solution-wide-build-configuration"></a>Úprava konfigurace sestavení v rámci řešení

1. Otevřete dialogové okno **Configuration Manager** .

2. V rozevíracím seznamu **Konfigurace aktivního řešení** vyberte konfiguraci, kterou chcete.

3. V podokně **kontexty projektu** pro každý projekt vyberte požadovanou **konfiguraci** a **platformu** a vyberte, zda má být **vytvořena** a zda má být **nasazena** .

## <a name="see-also"></a>Viz také
 [Principy konfigurací sestavení](../ide/understanding-build-configurations.md) [vytváření a čištění projektů a řešení v aplikaci Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md) [NIB postupy: Změna vlastností projektu a nastavení konfigurace](https://msdn.microsoft.com/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
