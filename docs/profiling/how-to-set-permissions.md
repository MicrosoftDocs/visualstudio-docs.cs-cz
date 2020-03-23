---
title: 'Postup: Nastavení oprávnění | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling, setting permissions
- security [Visual Studio ALM], setting permissions
- permissions [Visual Studio ALM], profiling
- profiling tools, setting profiling permissions
- performance tools, setting profiling permissions
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: c1ab7705c7ab46b07b08b707ce447f37c581036a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74774586"
---
# <a name="how-to-set-permissions"></a>Postup: Nastavení oprávnění

Tento článek popisuje, jak správce počítače uděluje oprávnění zabezpečení požadovaná pro profilování uživateli nebo skupině, která nemá oprávnění správce v tomto počítači.

Základní princip zabezpečení uvádí, že aplikace by měly být spuštěny s více než oprávnění, která potřebují. Tato zásada platí i pro uživatele. Pokud mohou být uživatelé plně efektivní, když jsou přihlášeni jako členové skupiny Users namísto skupiny Administrators, neměla by jim být udělena oprávnění správce. První postup "Chcete-li vytvořit uživatelský účet s uživatelskými oprávněními", popisuje, jak vytvořit uživatelský účet pro člena skupiny Users.

Členové skupiny Users budou potřebovat přístup ke složkám a souborům na disku, které jsou sdíleny s ostatními členy týmu. Druhý postup "Chcete-li udělit přístup ke sdíleným souborům projektu", popisuje, jak tento přístup udělit.

Členové skupiny Users mohou spustit nástroje profilování, pokud jim správce udělí přístup k softwarovému ovladači pro nástroje profilování. Poslední postup "Udělit přístup k ovladačprofilování," popisuje, jak udělit přístup k tomuto ovladači.

> [!NOTE]
> Chcete-li postupovat podle kroků uvedených v těchto postupech, potřebujete oprávnění správce.

## <a name="to-create-a-user-account-that-has-user-permissions"></a>Vytvoření uživatelského účtu s uživatelskými oprávněními

1. Klepněte pravým tlačítkem myši na **položku Tento počítač** a potom klepněte na příkaz **Spravovat**.

     Otevře se okno **Správa počítače.**

2. Rozbalte **položku Místní uživatelé a skupiny**.

3. Klepněte pravým tlačítkem myši na složku **Uživatelé** a potom klepněte na příkaz **Nový uživatel**.

     Zobrazí se dialogové okno **Nový uživatel.**

4. Dokončete pole v tomto dialogovém okně informacemi o uživatelském účtu, který vytváříte. Zadejte heslo. Volitelně zaškrtněte políčko, které vyžaduje, aby uživatel při příštím přihlášení změnil heslo.

5. Klepněte na tlačítko **Vytvořit** a potom na **tlačítko Zavřít**.

     Nový uživatel se zobrazí ve skupině Users, skupině uživatelů, kteří nemají oprávnění správce.

## <a name="to-grant-access-to-shared-project-files"></a>Udělení přístupu ke sdíleným souborům projektu

1. V Průzkumníkovi Windows (nebo Průzkumníku souborů) vyhledejte kořenový adresář stromu složek pro soubory projektu, které tento uživatel používá a sdílí projektový tým.

     Cesta k této složce se může podobat následujícímu:

    ```cmd
    D:\ourProject
    ```

2. Klepněte pravým tlačítkem myši na složku a potom klepněte na příkaz **Vlastnosti**.

     Zobrazí ** \<** se dialogové okno název> vlastnosti.

3. Klikněte na kartu **Zabezpečení**.

4. Klikněte na název uživatelského účtu v poli **Skupina nebo uživatelská jména.**

5. V poli **Oprávnění pro \<uživatelské jméno>** zaškrtněte políčko Úplné **řízení**.

6. Klikněte na tlačítko **OK**.

     To uděluje oprávnění uživateli pro strom sdílených složek, který začíná složky vybrané v kroku 5.

## <a name="to-grant-access-to-the-profiling-driver"></a>Udělení přístupu k ovladači profilování

1. Otevřete příkazový řádek jako správce.

2. Změňte adresář na:

    ```cmd
    <drive>:\Program Files\Microsoft Visual Studio 14\Team Tools\Performance Tools
    ```

3. Spusťte následující příkaz:

    ```cmd
    vsperfcmd /admin:driver,start /admin:service,start
    ```

     Tento příkaz nainstaluje a spustí ovladač pro profilovací nástroje.

     Tento příkaz spustí profilování ovladač a službu tak, aby uživatelé bez správce mohou používat funkce profilování, které jsou k dispozici v jejich uživatelském prostoru procesu. Příkaz může spustit pouze správce. a u uživatelů, kteří nejsou administrativními oprávněními, se nezdaří.

     Všimněte si, že účinky tohoto kroku jsou zpět po restartování počítače, pokud také provést poslední krok v tomto postupu.

4. Spuštěním příkazu povolíte přístup k funkcím ovladače profilování uživatelem nebo skupinou, která nemá přístup správce k počítači:

    ```cmd
    vsperfcmd /admin:security,allow,<right[,right],<user name|group name>
    ```

     Tento příkaz \<uděluje> \<uživatelskému jménu nebo> názvu skupiny přístup k nástrojům profilování. Správná \<možnost> určuje funkci profilování, ke které má uživatel přístup. Správná \<možnost> může být jedna nebo více z následujících hodnot:

    - FullAccess - umožňuje přístup ke všem metodám profilování, včetně shromažďování dat o výkonu ze služeb, vzorkování a profilování napříč relacemi.

    - SampleProfiling - umožňuje přístup k metodám profilování vzorků

    - CrossSession - umožňuje přístup k profilování mezi relacemi, které je vyžadováno pro profilování služeb.

5. (Nepovinné) Chcete-li zachovat výsledky některého z předchozích kroků po restartování počítače, spusťte následující příkaz:

    ```cmd
    vsperfcmd /admin:driver,autostart,on
    ```

   Zadali uživatelé po přihlášení budou nyní moci používat nástroje profilování bez oprávnění správce.

## <a name="see-also"></a>Viz také

[Konfigurace relací](../profiling/configuring-performance-sessions.md)
výkonu[Profilování VSPerfCmd](../profiling/vsperfcmd.md)
[a Zabezpečení systému Windows Vista](../profiling/profiling-and-windows-vista-security.md)
