---
title: ASP.NET Core webové aplikace pomocí Entity Framework & Visual Studio 2019
titleSuffix: ''
description: Jako první krok před vytvořením webové aplikace ASP.NET Core se naučíte, jak nainstalovat Visual Studio 2019 s tímto výukovým kurzem a podrobnými pokyny.
ms.custom: get-started
ms.date: 03/31/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
monikerRange: vs-2019
ms.topic: tutorial
ms.devlang: CSharp
author: ardalis
ms.author: ornella
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: f6d069bfa462b8aa75fc9247c08b3662c4a445fd
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88801799"
---
# <a name="tutorial-create-your-first-aspnet-core-app-using-entity-framework-with-visual-studio-2019"></a>Kurz: Vytvoření první aplikace ASP.NET Core pomocí Entity Framework se sadou Visual Studio 2019

V tomto kurzu vytvoříte ASP.NET Core webovou aplikaci, která používá data, a nasadíte ji do Azure. Tento kurz se skládá z následujících kroků:

- [Krok 1: instalace sady Visual Studio 2019](#step-1-install-visual-studio-2019)
- [Krok 2: Vytvoření první ASP.NET Core webové aplikace](tutorial-aspnet-core-ef-step-02.md)
- [Krok 3: práce s daty pomocí Entity Framework](tutorial-aspnet-core-ef-step-03.md)
- [Krok 4: vystavení webového rozhraní API z aplikace ASP.NET Core](tutorial-aspnet-core-ef-step-04.md)
- [Krok 5: nasazení aplikace ASP.NET Core do Azure](tutorial-aspnet-core-ef-step-05.md)

## <a name="step-1-install-visual-studio-2019"></a>Krok 1: instalace sady Visual Studio 2019

Přečtěte si, jak nainstalovat Visual Studio 2019 s tímto výukovým kurzem a podrobnými pokyny. Pokud jste již nainstalovali aplikaci Visual Studio, přeskočte dopředu ke [kroku 2: Vytvoření první webové aplikace ASP.NET Core](tutorial-aspnet-core-ef-step-02.md).

_Podívejte se na toto video a postupujte podle pokynů k instalaci sady Visual Studio a vytvoření první aplikace ASP.NET Core._

> [!VIDEO https://www.youtube.com/embed/Fz_HAqQGLtY]

## <a name="download-the-installer"></a>Stažení instalačního programu

Pokud chcete najít instalační program, navštivte [VisualStudio.com](https://visualstudio.com) . Vyhledejte odkaz Visual Studio 2019 a kliknutím na něj spusťte stahování. V případě bezplatné verze sady Visual Studio vyberte možnost Visual Studio Community.

## <a name="start-the-installer"></a>Spuštění instalačního programu

Po dokončení stahování spusťte instalační program kliknutím na tlačítko **Spustit** .

![Instalační program sady Visual Studio 2019](media/vs-2019/vs2019-installer.png)

## <a name="choose-workloads"></a>Zvolit úlohy

Sadu Visual Studio lze použít pro mnoho různých druhů vývoje a úlohy usnadňují stažení všeho, co potřebujete, pro druh aplikací, které chcete sestavit. Pro teď vyberte **ASP.NET a vývoj pro web** a vývojové úlohy **.NET Core pro různé platformy** . Instalační program můžete kdykoli znovu spustit později a nainstalovat další úlohy a součásti.

![Visual Studio 2019 – výběr úloh](media/vs-2019/vs2019-choose-workloads.png)

## <a name="install"></a>Instalace

Klikněte na **nainstalovat** a umožněte instalačnímu programu stažení a instalaci sady Visual Studio.

## <a name="run-visual-studio-for-the-first-time"></a>První spuštění sady Visual Studio

Po dokončení instalačního programu se aplikace Visual Studio spustí automaticky. Může se zobrazit výzva k přihlášení, která obsahuje některé skvělé funkce, které jsou k němu přidružené, ale teď se můžete rozhodnout, že to uděláte později. Dále můžete zvolit svůj motiv a nastavení vývoje. Jakmile provedete tyto volby, budete připraveni začít s prvním projektem. Klikněte na **vytvořit nový projekt** a pak zvolte **ASP.NET Core webová aplikace**.

![Visual Studio 2019 vytvoření nového projektu webové aplikace ASP.NET Core](media/vs-2019/vs2019-create-new-project.png)

## <a name="explore-aspnet-core-project-types"></a>Prozkoumat ASP.NET Core typy projektů

Můžete zvolit název projektu a umístění a pak vybrat **vytvořit**. Teď vyberte šablonu, která se má použít pro vaši aplikaci ASP.NET Core. Máte na výběr z následujících možností:

- Obsahovat. Prázdná šablona projektu, která vám umožní začít od začátku.
- API. Nejvhodnější pro webová rozhraní API.
- Webová aplikace Standardní ASP.NET Core webová aplikace vytvořená pomocí Razor Pages.
- Webová aplikace (Model-View-Controller). Standardní ASP.NET Core webové aplikace pomocí vzoru Model-View-Controller.
- Angular.
- React.js.
- React.js/Redux.
- Knihovna tříd Razor Používá se ke sdílení prostředků Razor mezi projekty.

Všimněte si, že pro většinu šablon projektů můžete také vybrat možnost povolit podporu Docker tím, že zaškrtnete políčko. Podporu ověřování můžete také přidat kliknutím na tlačítko změnit ověřování. Odtud si můžete vybrat z těchto:

- Bez ověřování.
- Jednotlivé uživatelské účty. Tyto jsou uložené v místní databázi nebo databázi založené na Azure.
- Pracovní nebo školní účty. Tato možnost pro ověřování používá službu Active Directory, Azure AD nebo Microsoft 365.
- Ověřování systému Windows. Vhodné pro intranetové aplikace.

Vyberte šablonu standardní webové aplikace bez ověřování a klikněte na **vytvořit**.

![Visual Studio 2019 volba možností projektu ASP.NET Core](media/vs-2019/vs2019-choose-aspnetcore-project.png)

## <a name="next-steps"></a>Další kroky

V dalším videu se dozvíte víc o vašem prvním ASP.NET Core projektu.

[Kurz: Vytvoření první ASP.NET Core webové aplikace](tutorial-aspnet-core-ef-step-02.md)

## <a name="see-also"></a>Viz také

- [Kurz: Začínáme s C# a ASP.NET Core](tutorial-aspnet-core.md) Podrobnější kurz bez návodu k videu
