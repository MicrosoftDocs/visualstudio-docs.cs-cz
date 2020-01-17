---
title: 'Postupy: vyloučení projektů ze sestavení'
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
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114800"
---
# <a name="how-to-exclude-projects-from-a-build"></a>Postupy: vyloučení projektů ze sestavení

Můžete sestavit řešení bez nutnosti sestavovat všechny projekty, které obsahuje. Můžete například vyloučit projekt, který přerušuje sestavení. Po prozkoumání a vyřešení problémů pak můžete sestavit projekt.

Projekt můžete vyloučit provedením následujících přístupů:

- Dočasné odebrání z aktivní konfigurace řešení.

- Vytvoření konfigurace řešení, která nezahrnuje projekt.

Další informace najdete v tématu [Principy konfigurací sestavení](../ide/understanding-build-configurations.md).

## <a name="to-temporarily-remove-a-project-from-the-active-solution-configuration"></a>Dočasné odebrání projektu z aktivní konfigurace řešení

1. Na panelu nabídek vyberte možnost **sestavit** > **Configuration Manager**.

2. V tabulce **kontexty projektu** vyhledejte projekt, který chcete ze sestavení vyloučit.

3. Ve sloupci **sestavení** projektu zrušte zaškrtnutí políčka.

4. Klikněte na tlačítko **Zavřít** a pak znovu sestavte řešení.

## <a name="to-create-a-solution-configuration-that-excludes-a-project"></a>Vytvoření konfigurace řešení, která vylučuje projekt

1. Na panelu nabídek vyberte možnost **sestavit** > **Configuration Manager**.

2. V seznamu **aktivní konfigurace řešení** vyberte možnost **\<nový >** .

3. Do pole **název** zadejte název pro konfiguraci řešení.

4. V seznamu **Kopírovat nastavení z** vyberte konfiguraci řešení, na které chcete založit novou konfiguraci (například **ladit**), a pak klikněte na tlačítko **OK** .

5. V dialogovém okně **Configuration Manager** zrušte zaškrtnutí políčka ve sloupci **sestavení** pro projekt, který chcete vyloučit, a poté klikněte na tlačítko **Zavřít** .

6. Na **standardním** panelu nástrojů ověřte, zda je nová konfigurace řešení aktivní konfigurace v poli **Konfigurace řešení** .

7. V panelu nabídky zvolte **sestavení** > **znovu sestavit řešení**.

## <a name="skipped-projects"></a>Přeskočené projekty

Projekty mohou být během sestavení přeskočeny, protože nejsou aktuální nebo protože jsou vyloučeny z konfigurace. Visual Studio používá MSBuild k sestavení vašich projektů. Nástroj MSBuild sestaví cíl pouze v případě, že výstup je starší než vstup, jak určuje časová razítka souborů. K vynucení opětovného sestavení použijte příkaz **sestavit** > znovu **Sestavit řešení**.

V podokně **sestavení** v okně **výstup** hlásí Visual Studio počet projektů, které byly aktuální, číslo, které bylo úspěšně sestaveno, číslo, které selhalo, a číslo, které bylo vynecháno. Počet vynechaných prvků nezahrnuje projekty, které nebyly vytvořeny, protože byly aktuální. Když jsou projekty vyloučeny z aktivní konfigurace, jsou během sestavení přeskočeny. Ve výstupu sestavení se zobrazí zpráva oznamující, že se projekt přeskočí:

```output
2>------ Skipped Build: Project: ConsoleApp2, Configuration: Debug x86 ------
2>Project not selected to build for this solution configuration
```

Chcete-li zjistit, proč byl projekt přeskočen, poznamenejte si aktivní konfiguraci (`Debug x86` v předchozím příkladu) a vyberte možnost **sestavit** > **Configuration Manager**. Můžete zobrazit nebo změnit, které projekty jsou přeskočeny pro každou konfiguraci, jak je popsáno v tomto článku.

## <a name="see-also"></a>Viz také:

- [Principy konfigurací sestavení](../ide/understanding-build-configurations.md)
- [Postupy: vytváření a úpravy konfigurací](../ide/how-to-create-and-edit-configurations.md)
- [Postupy: sestavení více konfigurací současně](../ide/how-to-build-multiple-configurations-simultaneously.md)
