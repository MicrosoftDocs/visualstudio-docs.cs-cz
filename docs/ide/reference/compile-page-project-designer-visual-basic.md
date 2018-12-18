---
title: Stránka Kompilovat, návrhář projektu (Visual Basic)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesCompile
helpviewer_keywords:
- compilation, Visual Basic projects
- compilation, options [Visual Basic]
- compilers, Visual Basic options
- compilation, instructions [Visual Basic]
- compiler options, Visual Basic
- Project Designer, Compile page
- Compile page in Project Designer
ms.assetid: b2a80230-906e-4e85-b3e0-fcd9c40426e1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6d1b5c55c3bc1732d0b394473f25c0b103c917f4
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38808371"
---
# <a name="compile-page-project-designer-visual-basic"></a>Stránka Kompilovat, návrhář projektu (Visual Basic)

Použití **kompilaci** stránky Návrháře projektu uvést pokyny kompilace. Na této stránce můžete také zadat kompilátoru pokročilé možnosti a před sestavením nebo po sestavení událostí.

Pro přístup k **kompilaci** zvolte uzel projektu (ne **řešení** uzlu) v **Průzkumníku řešení**. Klikněte na tlačítko **projektu**, **vlastnosti** na řádku nabídek. Jakmile se zobrazí Návrhář projektu, klikněte na tlačítko **kompilaci** kartu.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="configuration-and-platform"></a>Konfigurace a platforma

Tato nastavení umožňují vybrat konfigurace a platformy k zobrazení a úpravě.

> [!NOTE]
> Pomocí zjednodušených konfigurací sestavení systém projektu určuje, jestli se má sestavení ladění nebo vydání verze. Proto **konfigurace** a **platformy** seznamy se nezobrazují.

 **Konfigurace**

 Určuje které nastavení konfigurace má být zobrazeno nebo upraveno. Nastavení musí být **ladění** (výchozí), **vydání**, nebo **všechny konfigurace**. Další informace najdete v tématu [Principy konfigurací sestavení](../../ide/understanding-build-configurations.md) a [postupy: vytvoření a úprava konfigurací](../../ide/how-to-create-and-edit-configurations.md).

 **Platforma**

 Určuje které nastavení platformy má být zobrazeno nebo upraveno. Můžete zadat **jakýkoli procesor** (výchozí), **x64**, nebo **x86**.

## <a name="compiler-configuration-options"></a>Konfigurace možností kompilátoru

Tato nastavení umožňují nastavit kompilátor možnosti konfigurace.

 **Výstupní cesta sestavení**

 Určuje umístění výstupních souborů pro tuto konfiguraci projektu. Zadejte cestu k výstupu sestavení v tomto poli, nebo klikněte na tlačítko **Procházet** tlačítko a vyberte cestu. Všimněte si, že cesta je relativní; Pokud zadáte absolutní cestu, bude uložena jako relativní. Výchozí cesta je bin\Debug\ nebo bin\Release\\.

 Pomocí zjednodušených konfigurací sestavení systém projektu určuje, jestli se má sestavení ladění nebo vydání verze. **Sestavení** příkaz **ladění** nabídky (F5) vloží sestavení do místa ladění bez ohledu na to **výstupní cesta** zadáte. Ale **sestavení** příkaz **sestavení** nabídky se vloží do umístění, které zadáte.
  
 **Možnost explicit**  
 Určuje, jestli se má povolit implicitní deklaraci proměnných. Vyberte **na** tak, aby vyžadovala explicitní deklaraci proměnných. To způsobí, že kompilátor pro hlášení chyb Pokud proměnné nejsou deklarovány před jejich použití. Vyberte **vypnout** povolit implicitní deklaraci proměnných.  
  
 Toto nastavení odpovídá [/optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit) – možnost kompilátoru.  
  
 Pokud soubor zdrojového kódu obsahuje [Option Explicit – příkaz](/dotnet/visual-basic/language-reference/statements/option-explicit-statement), `On` nebo `Off` hodnota v příkazu přepíše **Option Explicit** nastavení **kompilace stránka**.  
  
 Když vytvoříte nový projekt **Option Explicit** nastavení **kompilace stránky** je nastavena na hodnotu **Option Explicit** nastavení **možnosti**  dialogové okno. Chcete-li zobrazit nebo změnit nastavení v tomto dialogovém okně na **nástroje** nabídky, klikněte na tlačítko **možnosti**. V **možnosti** dialogového okna rozbalte **projekty a řešení**a potom klikněte na tlačítko **VB výchozí**. Počáteční výchozí nastavení **Option Explicit** v **výchozí hodnoty pro VB** je **na**.  
  
 Nastavení **Option Explicit** k `Off` není obvykle vhodné. Název proměnné v jedné nebo více umístění, což způsobilo neočekávané výsledky při spuštění programu může mít překlep.  
  
 **Možnost strict**  
Určuje, jestli se má vynutí sémantiku přísného typu. Když **Option Strict** je **na**, následujících podmínek způsobit chybu kompilace:  
  
-   Implicitní zužující převody  
  
-   Pozdní vazba  
  
-   Implicitního zápisu, která vede `Object` typu  
  
Implicitní zužující převod chybám dochází při konverzi typu implicitní data, která je zužující převod. Další informace najdete v tématu [Option Strict – příkaz](/dotnet/visual-basic/language-reference/statements/option-strict-statement), [implicitní a explicitní převody](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions), a [Widening a zúžení převodů](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions).  
  
Objekt je přiřazeno k vlastnosti nebo metody, která je deklarována se typ proměnné pozdní vazby `Object`. Další informace najdete v tématu [Option Strict – příkaz](/dotnet/visual-basic/language-reference/statements/option-strict-statement) a [včasného a pozdní vazby](/dotnet/visual-basic/programming-guide/language-features/early-late-binding).
  
Implicitní typ chybám dochází, když odpovídající typ se nedá odvodit deklarované proměnné, tak typu `Object` je odvozen. To dochází především při použití `Dim` příkaz k deklaraci proměnné bez použití `As` klauzule a `Option Infer` je vypnuté. Další informace najdete v tématu [Option Strict – příkaz](/dotnet/visual-basic/language-reference/statements/option-strict-statement), [Option Infer – příkaz](/dotnet/visual-basic/language-reference/statements/option-infer-statement)a [specifikace jazyka Visual Basic](/dotnet/visual-basic/reference/language-specification).  
  
**Option Strict** nastavení odpovídá [/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) – možnost kompilátoru.  
  
Pokud soubor zdrojového kódu obsahuje [Option Strict – příkaz](/dotnet/visual-basic/language-reference/statements/option-strict-statement), `On` nebo `Off` hodnota v příkazu přepíše **Option Strict** nastavení **kompilace stránky** .  
  
Při vytváření projektu, **Option Strict** nastavení **kompilace stránky** je nastavena na hodnotu **Option Strict** nastavení **možnosti** dialogové okno. Chcete-li zobrazit nebo změnit nastavení v tomto dialogovém okně na **nástroje** nabídky, klikněte na tlačítko **možnosti**. V **možnosti** dialogového okna rozbalte **projekty a řešení**a potom klikněte na tlačítko **VB výchozí**. Počáteční výchozí nastavení **Option Strict** v **výchozí hodnoty pro VB** je **vypnout**.  
  
**Možnost Strict jednotlivých upozornění.** **Upozornění konfigurace** část **kompilace stránky** má nastavení, které odpovídají uvedených tří podmínek, které způsobí chybu kompilace při `Option Strict` zapnutý. Tato nastavení jsou následující:  
  
-   **Implicitní převod**  
  
-   **Pozdní vazba. volání by mohlo selhat v době běhu**  
  
-   **Implicitní typ; převzatý objekt**  
  
Pokud nastavíte **Option Strict** k **na**, všechna tři nastavení konfigurace upozornění jsou nastaveny na **chyba**. Pokud nastavíte **Option Strict** k **vypnout**, všechny tři nastavení **žádný**.  
  
Samostatně můžete změnit nastavení každé upozornění konfigurace **žádný**, **upozornění**, nebo **chyba**. Pokud mají všechny tři nastavení konfigurace upozornění **chyba**, `On` se zobrazí v `Option strict` pole. Pokud mají všechny tři **žádný**, `Off` se zobrazí v tomto poli. Pro libovolnou kombinaci těchto nastavení **(vlastní)** se zobrazí.  
  
**Možnost compare**  
Určuje typ porovnání řetězců k použití. Vyberte **binární** dáte pokyn, aby kompilátor používal porovnávání řetězců binární, velká a malá písmena. Vyberte **Text** použít porovnávání řetězců specifické pro národní prostředí, nerozlišuje velikost písmen textu.  
  
Toto nastavení odpovídá [/optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare) – možnost kompilátoru.  
  
Pokud soubor zdrojového kódu obsahuje [možnost porovnat příkaz](/dotnet/visual-basic/language-reference/statements/option-compare-statement), `Binary` nebo `Text` hodnota v příkazu přepíše **Option Compare** nastavení na **kompilace stránka**.  
  
Při vytváření projektu, **Option Compare** nastavení **kompilace stránky** je nastavena na hodnotu **Option Compare** nastavení **možnosti** dialogové okno. Chcete-li zobrazit nebo změnit nastavení v tomto dialogovém okně na **nástroje** nabídky, klikněte na tlačítko **možnosti**. V **možnosti** dialogového okna rozbalte **projekty a řešení**a potom klikněte na tlačítko **VB výchozí**. Počáteční výchozí nastavení **Option Compare** v **výchozí hodnoty pro VB** je **binární**.  
  
**Možnost infer**  
Určuje, jestli se má povolit odvození místního typu v deklaraci proměnných. Vyberte **na** k povolení použití odvození místního typu. Vyberte **vypnout** k odvození místního typu blok.  
  
Toto nastavení odpovídá [/optioninfer](/dotnet/visual-basic/reference/command-line-compiler/optioninfer) – možnost kompilátoru.  
  
Pokud soubor zdrojového kódu obsahuje [Option Infer – příkaz](/dotnet/visual-basic/language-reference/statements/option-infer-statement), `On` nebo `Off` hodnota v příkazu přepíše **Option Infer** nastavení **kompilace stránky** .  
  
Při vytváření projektu, **Option Infer** nastavení **kompilace stránky** je nastavena na hodnotu **Option Infer** nastavení **možnosti**dialogové okno. Chcete-li zobrazit nebo změnit nastavení v tomto dialogovém okně na **nástroje** nabídky, klikněte na tlačítko **možnosti**. V **možnosti** dialogového okna rozbalte **projekty a řešení**a potom klikněte na tlačítko **VB výchozí**. Počáteční výchozí nastavení **Option Infer** v **výchozí hodnoty pro VB** je **na**.  
  
**Cíl CPU**  
Určuje procesor, který bude cílen výstupním souborem. Zadejte **x86** pro jakýkoli procesor kompatibilní s verzí Intel 32-bit **x64** pro jakýkoli procesor kompatibilní s verzí Intel 64-bit **ARM** pro jakýkoli procesor ARM nebo **jakýkoli procesor**  k určení, že je přijatelný jakýkoli procesor. **Jakýkoli procesor** je výchozí hodnota pro nové projekty, protože umožňuje aplikaci, aby běžela na největší počet typů hardwaru.  
  
Další informace najdete v tématu [/Platform (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/platform).  
  
**Preferovat 32 bitů**  
Pokud **preferovat 32bitovou verzi** zaškrtávací políčko zaškrtnuto, aplikace běží jako 32bitová aplikace ve 32bitové a 64bitové verze Windows. V opačném případě aplikace běží jako 32bitová aplikace ve 32bitové verze Windows a jako na 64bitovými verzemi Windows 64-bit aplikace.  
  
Spuštění aplikace 64-bit zdvojnásobuje velikost ukazatele, a to může způsobit problémy s kompatibilitou s knihovnami, které jsou výhradně 32bitové. Je vhodné spustit aplikaci jako 64-bit pouze v případě, že je výrazně rychlejší spuštění, nebo potřebuje více než 4 GB paměti.  
  
Toto zaškrtávací políčko je dostupné jenom v případě, že jsou splněny všechny následující podmínky:  
  
-   Na **stránka kompilovat**, **cílový procesor** seznamu je nastavena na **jakýkoli procesor**.  
  
-   Na **stránky aplikace**, **typ aplikace** seznam určuje, že projekt je aplikace.  
  
-   Na **stránky aplikace**, **Cílová architektura** seznamu určuje rozhraní .NET Framework 4.5.  
  
**Konfigurace upozornění**  
Tato tabulka shrnuje sestavení podmínky a odpovídající úroveň oznámení **žádný**, **upozornění**, nebo **chyba** pro každý.  
  
Ve výchozím nastavení všechna upozornění kompilátoru přidají do seznamu úkolů během kompilace. Vyberte **zakázat všechna upozornění** dáte pokyn kompilátoru, aby problém upozornění a chyby. Vyberte **považovat všechna upozornění jako chyby** Pokud chcete, aby kompilátor zpracovávat upozornění jako chyby, které je potřeba opravit.  
  
**Zakázat všechna upozornění**  
Určuje, jestli chce použít kompilátor, aby uvedená v upozornění na problémy **podmínku a oznámení** tabulky popsané dříve v tomto dokumentu. Ve výchozím nastavení je toto políčko zaškrtnuté. Toto políčko zaškrtnuto, abyste instruovali kompilátor není vydat upozornění a chyby.  
  
Toto nastavení odpovídá [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) – možnost kompilátoru.  
  
**Považovat všechna upozornění jako chyby**  
Určuje, jak zpracovávat upozornění. Ve výchozím nastavení, toto zaškrtávací políčko zaškrtnuto, takže všechna upozornění oznámení zůstanou nastavená na **upozornění**. Zaškrtněte toto políčko, chcete-li změnit všechna oznámení upozornění pro **chyba**.  
  
Tato možnost je dostupná pouze tehdy, pokud **zakázat všechna upozornění** se vymaže.  
  
**Generovat soubor dokumentace XML**  
Určuje, jestli se má generovat informace o dokumentaci. Ve výchozím nastavení je toto políčko zaškrtnuto, že kompilátoru generovat informace o dokumentaci a zahrnout do souboru XML. Zrušte zaškrtnutí tohoto políčka, abyste instruovali kompilátor nechcete vytvářet dokumentaci.  
  
Toto nastavení odpovídá [/doc](/dotnet/visual-basic/reference/command-line-compiler/doc) – možnost kompilátoru.  
  
**Zaregistrovat pro interoperabilitu COM**  
Určuje, zda bude vaše spravovaná aplikace vystavovat objekt modelu COM (Obálka volatelná aplikacemi COM) umožňující objektu modelu COM interakci s aplikací.  
  
Ve výchozím nastavení je toto zaškrtávací políčko zaškrtnuto, který určuje, že aplikace nebude umožňovat komunikace s objekty COM. Vyberte toto zaškrtávací políčko pro povolení komunikace s objekty COM.  
  
Tato možnost není k dispozici pro projekty aplikací pro Windows nebo konzolové aplikace.  
  
**Události sestavení**  
Kliknutím na toto tlačítko přístup **události sestavení** dialogové okno. Použijte toto dialogové okno k určení pokyny ke konfiguraci před a po sestavení projektu. Toto dialogové okno se vztahují na projekty Visual Basic pouze. Další informace najdete v tématu [sestavení dialogové okno události (Visual Basic)](../../ide/reference/build-events-dialog-box-visual-basic.md).  
  
**Možnosti rozšířené kompilace**  
Kliknutím na toto tlačítko přístup **AdvancedCompiler nastavení** dialogové okno. Použití **AdvancedCompiler nastavení** dialogové okno k zadání projekt rozšířenou vlastností konfigurace sestavení. Toto dialogové okno se vztahují na projekty Visual Basic pouze. Další informace najdete v tématu [Advanced kompilátoru dialogové okno nastavení (Visual Basic)](../../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md).  


## <a name="see-also"></a>Viz také:

- [Postupy: Určení událostí sestavení (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)
- [Kompilátor příkazového řádku jazyka Visual Basic](/dotnet/visual-basic/reference/command-line-compiler/index)
- [Postupy: Vytvoření a úprava konfigurací](../../ide/how-to-create-and-edit-configurations.md)