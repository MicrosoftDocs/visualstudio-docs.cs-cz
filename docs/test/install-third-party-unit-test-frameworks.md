---
title: Instalace systémů testování částí od třetích stran
ms.date: 04/01/2019
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: b70e26adc7c0c9a8dc409d9b4b971b233418b8e1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594276"
---
# <a name="install-unit-test-frameworks"></a>Instalace rozhraní testování částí

Visual Studio Test Explorer můžete spustit testy z libovolného rozhraní testování částí, který vyvinul rozhraní adaptéru pro něj. Instalace rozhraní framework zkopíruje binární soubory a přidá šablony projektů sady Visual Studio pro jazyky, které podporuje. Při vytváření projektu se šablonou je rámec zaregistrován pomocí Průzkumníka testů.

Řešení visual studio může obsahovat projekty testování částí, které používají různé architektury a které jsou zaměřeny na různé jazyky.

[MSTest](getting-started-with-unit-testing.md) je testovací rozhraní poskytované aplikací Visual Studio a je nainstalován ve výchozím nastavení.

## <a name="acquire-frameworks"></a>Získat rámce

Nainstalujte rozhraní testování částí jiných výrobců pomocí **Správce balíčků NuGet**.

1. Klikněte pravým tlačítkem myši na projekt, který bude obsahovat testovací kód, a vyberte **spravovat balíčky NuGet**.

2. Ve **Správci balíčků NuGet**vyhledejte testovací architekturu, kterou chcete nainstalovat, a klepněte na tlačítko **Instalovat**.

   ![Správce balíčků NuGet v sadě Visual Studio](media/vs-2019/nuget-package-manager.png)

## <a name="update-to-the-latest-test-adapters"></a>Aktualizace nejnovějších testovacích adaptérů

Aktualizujte na nejnovější stabilní testovací adaptér, abyste měli lepší zjišťování a spouštění testů. Další informace o aktualizacích testovacích adaptérů MSTest, NUnit a xUnit naleznete v [blogu sady Visual Studio](https://devblogs.microsoft.com/visualstudio/test-experience-improvements/).

### <a name="to-update-to-the-latest-stable-test-adapter-version"></a>Aktualizace na nejnovější verzi stabilního testovacího adaptéru

1. Otevřete Správce balíčků Nuget pro vaše řešení přechodem na **nástroje** > **NuGet Správce** > balíčků**Spravovat balíčky NuGet pro řešení**.

2. Klikněte na kartu **Aktualizace** a vyhledejte nainstalované adaptéry MSTest, NUnit nebo xUnit.

3. Vyberte každý testovací adaptér a v rozevírací nabídce vyberte nejnovější stabilní verzi.

4. Zvolte tlačítko **Instalovat.**

   ![Upgrade testovacího adaptéru](media/install-adapter-upgrade.png)

## <a name="see-also"></a>Viz také

- [Testování částí kódu](../test/unit-test-your-code.md)
