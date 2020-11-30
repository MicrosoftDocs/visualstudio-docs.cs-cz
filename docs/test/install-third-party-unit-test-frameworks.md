---
title: Instalace systémů testování částí od třetích stran
description: Průzkumník testů sady Visual Studio může spouštět testy z libovolného rozhraní pro testování částí, které pro něj vyvinulo rozhraní adaptéru.
ms.custom: SEO-VS-2020
ms.date: 07/09/2020
ms.topic: how-to
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: e6433d665157c186a390e2963ef7ad1447b2f982
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/30/2020
ms.locfileid: "96329975"
---
# <a name="install-unit-test-frameworks"></a>Nainstalovat rozhraní pro testování částí

Průzkumník testů sady Visual Studio může spouštět testy z libovolného rozhraní pro testování částí, které pro něj vyvinulo rozhraní adaptéru. Instalace rozhraní zkopíruje binární soubory a přidá šablony projektů sady Visual Studio pro jazyky, které podporuje. Při vytváření projektu se šablonou je rozhraní registrováno v Průzkumníku testů.

Řešení sady Visual Studio může obsahovat projekty testování částí, které používají různá rozhraní a cílí na různé jazyky.

::: moniker range=">=vs-2019"
Pro .NET, [MSTest, nunit a xUnit](getting-started-with-unit-testing.md) jsou testovací architektury poskytované aplikací Visual Studio, které jsou nainstalovány ve výchozím nastavení.
::: moniker-end
::: moniker range="vs-2017"
[MSTest](getting-started-with-unit-testing.md) je testovací rozhraní, které poskytuje Visual Studio a ve výchozím nastavení je nainstalované.
::: moniker-end

## <a name="acquire-frameworks"></a>Získat rozhraní

Nainstalujte rozhraní pro testování částí od třetích stran pomocí **Správce balíčků NuGet**.

1. Klikněte pravým tlačítkem na projekt, který bude obsahovat testovací kód a vyberte možnost **Spravovat balíčky NuGet**.

2. Ve **Správci balíčků NuGet** vyhledejte testovací rozhraní, které chcete nainstalovat, a pak klikněte na **nainstalovat**.

   ![Správce balíčků NuGet v aplikaci Visual Studio](media/vs-2019/nuget-package-manager.png)

## <a name="update-to-the-latest-test-adapters"></a>Aktualizace na nejnovější adaptéry testů

Aktualizujte na nejnovější stabilní testovací adaptér a vyzkoušejte si lepší zjišťování a provádění testů. Další informace o aktualizacích adaptérů MSTest, NUnit a xUnit test Adapters najdete v [blogu sady Visual Studio](https://devblogs.microsoft.com/visualstudio/test-experience-improvements/).

### <a name="to-update-to-the-latest-stable-test-adapter-version"></a>Aktualizace na nejnovější verzi stabilního testovacího adaptéru

1. Otevřete Správce balíčků NuGet pro vaše řešení, a to tak, že přejdete na **nástroje**  >  **Správce balíčků NuGet**  >  **Spravovat balíčky NuGet pro řešení**.

2. Klikněte na kartu **aktualizace** a vyhledejte adaptéry MSTest, NUnit nebo xUnit test Adapters, které jsou nainstalovány.

3. Vyberte jednotlivé adaptéry testů a v rozevírací nabídce vyberte nejnovější stabilní verzi.

4. Klikněte na tlačítko **instalovat** .

   ![Upgrade testovacího adaptéru](media/install-adapter-upgrade.png)

## <a name="see-also"></a>Viz také

- [Testování částí kódu](../test/unit-test-your-code.md)
