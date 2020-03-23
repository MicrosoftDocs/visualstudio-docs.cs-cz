---
title: 'Postup: Vyloučení projektů z sestavení'
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
ms.assetid: 17a837ca-5db9-46cd-b5a7-b14ad1d2c47d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a19c49482c45aa0a3cf5d7cb33eb106adb65b83b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114800"
---
# <a name="how-to-exclude-projects-from-a-build"></a>Postup: Vyloučení projektů z sestavení

Můžete vytvořit řešení bez vytváření všech projektů, které obsahuje. Můžete například vyloučit projekt, který přeruší sestavení. Potom můžete vytvořit projekt po prozkoumání a řešení problémů.

Projekt můžete vyloučit následujícím postupem:

- Dočasně jej odebere z konfigurace aktivního řešení.

- Vytvoření konfigurace řešení, která nezahrnuje projekt.

Další informace naleznete v [tématu Understand build configurations](../ide/understanding-build-configurations.md).

## <a name="to-temporarily-remove-a-project-from-the-active-solution-configuration"></a>Dočasné odebrání projektu z konfigurace aktivního řešení

1. Na řádku nabídek zvolte **Build** > **Configuration Manager**.

2. V tabulce **Kontexty projektu** vyhledejte projekt, který chcete vyloučit ze sestavení.

3. Ve sloupci **Sestavení** pro projekt zrušte zaškrtnutí políčka.

4. Zvolte tlačítko **Zavřít** a potom znovu vytvořte řešení.

## <a name="to-create-a-solution-configuration-that-excludes-a-project"></a>Vytvoření konfigurace řešení, která vylučuje projekt

1. Na řádku nabídek zvolte **Build** > **Configuration Manager**.

2. V seznamu **Konfigurace aktivního řešení** zvolte ** \<Nový>**.

3. Do pole **Název** zadejte název konfigurace řešení.

4. V **seznamu Kopírovat nastavení ze** zvolte konfiguraci řešení, na které chcete založit novou konfiguraci (například **Ladění**), a pak zvolte tlačítko **OK.**

5. V dialogovém okně **Správce konfigurace** zrušte zaškrtnutí políčka ve sloupci **Sestavení** pro projekt, který chcete vyloučit, a pak zvolte tlačítko **Zavřít.**

6. Na panelu nástrojů **Standard** ověřte, zda je nová konfigurace řešení aktivní konfigurací v poli **Konfigurace řešení.**

7. Na řádku nabídek zvolte **Build** > **Rebuild Solution**.

## <a name="skipped-projects"></a>Přeskočené projekty

Projekty mohou být přeskočeny během sestavení, protože nejsou aktuální nebo protože jsou vyloučeny z konfigurace. Visual Studio používá MSBuild k vytváření projektů. MSBuild vytvoří cíl pouze v případě, že výstup je starší než vstup, jak je určeno časovými razítky souboru. Chcete-li vynutit opětovné sestavení, použijte příkaz **Řešení** > **opětovného sestavení**.

V podokně **sestavení** **okna Výstup** Visual Studio hlásí počet projektů, které byly aktuální, počet, který byl úspěšně vytvořen, číslo, které se nezdařilo, a číslo, které byly přeskočeny. Přeskočený počet nezahrnuje projekty, které nebyly vytvořeny, protože byly aktuální. Pokud jsou projekty vyloučeny z aktivní konfigurace, jsou přeskočeny během sestavení. Ve výstupu sestavení se zobrazí zpráva označující, že projekt je přeskočen:

```output
2>------ Skipped Build: Project: ConsoleApp2, Configuration: Debug x86 ------
2>Project not selected to build for this solution configuration
```

Chcete-li zjistit, proč byl projekt přeskočen,`Debug x86` poznamenejte si aktivní konfiguraci (v předchozím příkladu) a zvolte Nástroj pro nástroj**Konfigurace** **sestavení** > . Můžete zobrazit nebo změnit, které projekty jsou přeskočeny pro každou konfiguraci, jak je popsáno v tomto článku.

## <a name="see-also"></a>Viz také

- [Vysvětlení konfigurací sestavení](../ide/understanding-build-configurations.md)
- [Postup: Vytváření a úpravy konfigurací](../ide/how-to-create-and-edit-configurations.md)
- [Postup: Vytvoření více konfigurací současně](../ide/how-to-build-multiple-configurations-simultaneously.md)
