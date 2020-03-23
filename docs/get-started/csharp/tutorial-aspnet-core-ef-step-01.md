---
title: ASP.NET základní webová aplikace s frameworkem entity & Visual Studia 2019
titleSuffix: ''
description: Jako první krok před vytvořením webové aplikace ASP.NET Core se dozvíte, jak nainstalovat Visual Studio 2019 s tímto kurzem v idea a podrobnými pokyny.
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
ms.openlocfilehash: d900c0f51b14450f38caf06738739daef2549235
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "77580098"
---
# <a name="tutorial-create-your-first-aspnet-core-app-using-entity-framework-with-visual-studio-2019"></a>Kurz: Vytvoření první ASP.NET základní aplikace pomocí entity Framework u Visual Studia 2019

V tomto kurzu vytvoříte ASP.NET webovou aplikaci Core, která používá data, a nasadíte je do Azure. Tento kurz se skládá z následujících kroků:

- [Krok 1: Instalace Visual Studia 2019](#step-1-install-visual-studio-2019)
- [Krok 2: Vytvoření první webové aplikace ASP.NET Core](tutorial-aspnet-core-ef-step-02.md)
- [Krok 3: Práce s daty pomocí entity Framework](tutorial-aspnet-core-ef-step-03.md)
- [Krok 4: Vystavení webového rozhraní API z aplikace ASP.NET Core](tutorial-aspnet-core-ef-step-04.md)
- [Krok 5: Nasazení aplikace ASP.NET Core do Azure](tutorial-aspnet-core-ef-step-05.md)

## <a name="step-1-install-visual-studio-2019"></a>Krok 1: Instalace Visual Studia 2019

Přečtěte si, jak nainstalovat Visual Studio 2019 s tímto kurzem k videu a podrobnými pokyny. Pokud jste už visual studio nainstalovali, přejděte na [krok 2: Vytvořte první ASP.NET základní webovou aplikaci](tutorial-aspnet-core-ef-step-02.md).

_Podívejte se na toto video a postupujte podle pokynů k instalaci Visual Studia a vytvoření první aplikace ASP.NET Core._

> [!VIDEO https://www.youtube.com/embed/Fz_HAqQGLtY]

## <a name="download-the-installer"></a>Stažení instalačního programu

Přejděte na [visualstudio.com](https://visualstudio.com) a vyhledejte instalační program. Vyhledejte odkaz Visual Studia 2019 a kliknutím na něj spusťte stahování. Pro bezplatnou verzi sady Visual Studio zvolte Visual Studio Community.

## <a name="start-the-installer"></a>Spuštění instalačního programu

Po dokončení stahování spusťte instalační program klepnutím na **tlačítko Spustit.**

![Instalační program Visual Studia 2019](media/vs-2019/vs2019-installer.png)

## <a name="choose-workloads"></a>Výběr úloh

Visual Studio lze použít pro mnoho různých druhů vývoje a úlohy usnadňují stahování všeho, co potřebujete pro typ aplikací, které chcete vytvářet. Zvolte **ASP.NET a vývoj webu** a .NET Core vývojové úlohy **napříč platformami** pro tuto chvíli. Instalační program můžete vždy později znovu spustit a nainstalovat další úlohy a součásti.

![Visual Studio 2019 Zvolit úlohy](media/vs-2019/vs2019-choose-workloads.png)

## <a name="install"></a>Instalace

Klikněte na **Nainstalovat** a nechte instalační program stáhnout a nainstalovat Visual Studio.

## <a name="run-visual-studio-for-the-first-time"></a>První spuštění sady Visual Studio

Visual Studio by se mělo spustit automaticky po dokončení instalačního programu. Můžete být vyzváni k přihlášení, což má některé pěkné funkce s ním spojené, ale nyní se můžete rozhodnout, že tak učiníte později. Dále si můžete vybrat téma a nastavení vývoje. Jakmile provedete tato rozhodnutí, budete připraveni zahájit svůj první projekt. Klepněte na tlačítko **Vytvořit nový projekt** a zvolte ASP.NET základní **webovou aplikaci**.

![Visual Studio 2019 Vytvořit nový ASP.NET základní projekt webové aplikace](media/vs-2019/vs2019-create-new-project.png)

## <a name="explore-aspnet-core-project-types"></a>Prozkoumejte ASP.NET základní typy projektů

Můžete zvolit název a umístění projektu a pak vybrat **Vytvořit**. Nyní zvolte šablonu, kterou chcete použít pro aplikaci ASP.NET Core. Máte na výběr z následujících možností:

- Prázdné. Prázdná šablona projektu, která umožňuje začít od začátku.
- Rozhraní api. Nejlepší pro webová api.
- Webová aplikace. Standardní ASP.NET Core webová aplikace vytvořená s Razor Pages.
- webová aplikace (Model-View-Controller). Standardní ASP.NET webovou aplikaci Core pomocí vzoru Model-View-Controller.
- Úhlové.
- Reagujte.js.
- React.js / Redux.
- Knihovna třídy Holicí strojek. Používá se ke sdílení datových zdrojů Razor mezi projekty.

Všimněte si, že pro většinu šablon projektu můžete také povolit podporu Dockeru zaškrtnutím políčka. Podporu ověřování můžete přidat také klepnutím na tlačítko Změnit ověřování. Odtud si můžete vybrat z:

- Bez ověřování.
- Jednotlivé uživatelské účty. Ty jsou uloženy v místní databázi nebo databázi založené na Azure.
- Pracovní nebo školní účty. Tato možnost používá pro ověřování službu Active Directory, Azure AD nebo Office 365.
- Ověřování systému Windows. Vhodné pro intranetové aplikace.

Vyberte standardní šablonu webové aplikace bez ověřování a klepněte na **tlačítko Vytvořit**.

![Visual Studio 2019 Zvolte ASP.NET základní možnosti projektu](media/vs-2019/vs2019-choose-aspnetcore-project.png)

## <a name="next-steps"></a>Další kroky

V dalším videu se dozvíte více o svém prvním projektu ASP.NET Core.

[Kurz: Vytvoření první ASP.NET základní webové aplikace](tutorial-aspnet-core-ef-step-02.md)

## <a name="see-also"></a>Viz také

- [Kurz: Začínáme s C# a ASP.NET Core](tutorial-aspnet-core.md) Podrobnější výukový program bez návodu k videu
