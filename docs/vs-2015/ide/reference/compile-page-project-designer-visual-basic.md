---
title: Stránka kompilovat, Návrhář (Visual Basic) projektu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 65
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4b369b1aa8d9e6857b29a5c37d13169b2e21ea74
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49924549"
---
# <a name="compile-page-project-designer-visual-basic"></a>Stránka Kompilovat, návrhář projektu (Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Použití **kompilaci** stránky Návrháře projektu uvést pokyny kompilace. Na této stránce můžete také zadat kompilátoru pokročilé možnosti a před sestavením nebo po sestavení událostí.  
  
 Pro přístup k **kompilaci** zvolte uzel projektu (ne **řešení** uzlu) v **Průzkumníku řešení**. Klikněte na tlačítko **projektu**, **vlastnosti** na řádku nabídek. Jakmile se zobrazí Návrhář projektu, klikněte na tlačítko **kompilaci** kartu.  
  
 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]  
  
## <a name="configuration-and-platform"></a>Konfigurace a platforma  
 Tato nastavení umožňují vybrat konfigurace a platformy k zobrazení a úpravě.  
  
> [!NOTE]
>  Pomocí zjednodušených konfigurací sestavení systém projektu určuje, jestli se má sestavení ladění nebo vydání verze. Proto **konfigurace** a **platformy** seznamy se nezobrazují. Další informace najdete v tématu [konfigurace ladění a verzí projektu](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e).  
  
 **Konfigurace**  
 Určuje které nastavení konfigurace má být zobrazeno nebo upraveno. Nastavení musí být **ladění** (výchozí), **vydání**, nebo **všechny konfigurace**. Další informace najdete v tématu [konfigurace ladění a verzí projektu](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e) a [postupy: vytvoření a úprava konfigurací](../../ide/how-to-create-and-edit-configurations.md).  
  
 **Platforma**  
 Určuje které nastavení platformy má být zobrazeno nebo upraveno. Můžete zadat **jakýkoli procesor** (výchozí), **x64**, nebo **x86**. Další informace najdete v tématu [konfigurace ladění a verzí projektu](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e).  
  
## <a name="compiler-configuration-options"></a>Konfigurace možností kompilátoru  
 Tato nastavení umožňují nastavit kompilátor možnosti konfigurace.  
  
 **Výstupní cesta sestavení**  
 Určuje umístění výstupních souborů pro tuto konfiguraci projektu. Zadejte cestu k výstupu sestavení v tomto poli, nebo klikněte na tlačítko **Procházet** tlačítko a vyberte cestu. Všimněte si, že cesta je relativní; Pokud zadáte absolutní cestu, bude uložena jako relativní. Výchozí cesta je bin\Debug\ nebo bin\Release\\. Další informace najdete v tématu [konfigurace ladění a verzí projektu](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e).  
  
 Pomocí zjednodušených konfigurací sestavení systém projektu určuje, jestli se má sestavení ladění nebo vydání verze. **Sestavení** příkaz **ladění** nabídky (F5) vloží sestavení do místa ladění bez ohledu na to **výstupní cesta** zadáte. Ale **sestavení** příkaz **sestavení** nabídky se vloží do umístění, které zadáte. Další informace najdete v tématu [konfigurace ladění a verzí projektu](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e).  
  
 **Možnost explicit**  
 Určuje, jestli se má povolit implicitní deklaraci proměnných. Vyberte **na** tak, aby vyžadovala explicitní deklaraci proměnných. To způsobí, že kompilátor pro hlášení chyb Pokud proměnné nejsou deklarovány před jejich použití. Vyberte **vypnout** povolit implicitní deklaraci proměnných.  
  
 Toto nastavení odpovídá [/optionexplicit](http://msdn.microsoft.com/library/5d296ab3-bafe-4c4d-9887-78f162ed86c7) – možnost kompilátoru.  
  
 Pokud soubor zdrojového kódu obsahuje [Option Explicit – příkaz](http://msdn.microsoft.com/library/e82ac1ad-2cd3-49b2-b985-8bcf016f3fcc), `On` nebo `Off` hodnota v příkazu přepíše **Option Explicit** nastavení **kompilace stránka**.  
  
 Když vytvoříte nový projekt **Option Explicit** nastavení **kompilace stránky** je nastavena na hodnotu **Option Explicit** nastavení **možnosti**  dialogové okno. Chcete-li zobrazit nebo změnit nastavení v tomto dialogovém okně na **nástroje** nabídky, klikněte na tlačítko **možnosti**. V **možnosti** dialogového okna rozbalte **projekty a řešení**a potom klikněte na tlačítko **VB výchozí**. Počáteční výchozí nastavení **Option Explicit** v **výchozí hodnoty pro VB** je **na**.  
  
 Nastavení **Option Explicit** k `Off` není obvykle vhodné. Název proměnné v jedné nebo více umístění, což způsobilo neočekávané výsledky při spuštění programu může mít překlep.  
  
 **Možnost strict**  
 Určuje, jestli se má vynutí sémantiku přísného typu. Když **Option Strict** je **na**, následujících podmínek způsobit chybu kompilace:  
  
- Implicitní zužující převody  
  
- Pozdní vazba  
  
- Implicitního zápisu, která vede `Object` typu  
  
  Implicitní zužující převod chybám dochází při konverzi typu implicitní data, která je zužující převod. Další informace najdete v tématu [Option Strict – příkaz](http://msdn.microsoft.com/library/5883e0c1-a920-4274-8e46-b0ff047eaee5), [implicitní a explicitní převody](http://msdn.microsoft.com/library/77de1659-af8a-492c-967e-e7ef60ccce66), a [Widening a zúžení převodů](http://msdn.microsoft.com/library/058c3152-6c28-4268-af44-2209e774f0bd).  
  
  Objekt je přiřazeno k vlastnosti nebo metody, která je deklarována se typ proměnné pozdní vazby `Object`. Další informace najdete v tématu [Option Strict – příkaz](http://msdn.microsoft.com/library/5883e0c1-a920-4274-8e46-b0ff047eaee5) a [včasného a pozdní vazby](http://msdn.microsoft.com/library/d6ff7f1e-b94f-4205-ab8d-5cfa91758724).  
  
  Implicitní typ chybám dochází, když odpovídající typ se nedá odvodit deklarované proměnné, tak typu `Object` je odvozen. To dochází především při použití `Dim` příkaz k deklaraci proměnné bez použití `As` klauzule a `Option Infer` je vypnuté. Další informace najdete v tématu [Option Strict – příkaz](http://msdn.microsoft.com/library/5883e0c1-a920-4274-8e46-b0ff047eaee5), [Option Infer – příkaz](http://msdn.microsoft.com/library/4ad3e6e9-8f5b-4209-a248-de22ef6e4652)a [specifikace jazyka Visual Basic](http://msdn.microsoft.com/library/42c30017-19d0-442e-87a2-850b66ddc3df).  
  
  **Option Strict** nastavení odpovídá [/optionstrict](http://msdn.microsoft.com/library/c7b10086-0fa4-49db-b3c8-4ae0db5957da) – možnost kompilátoru.  
  
  Pokud soubor zdrojového kódu obsahuje [Option Strict – příkaz](http://msdn.microsoft.com/library/5883e0c1-a920-4274-8e46-b0ff047eaee5), `On` nebo `Off` hodnota v příkazu přepíše **Option Strict** nastavení **kompilace stránky** .  
  
  Při vytváření projektu, **Option Strict** nastavení **kompilace stránky** je nastavena na hodnotu **Option Strict** nastavení **možnosti** dialogové okno. Chcete-li zobrazit nebo změnit nastavení v tomto dialogovém okně na **nástroje** nabídky, klikněte na tlačítko **možnosti**. V **možnosti** dialogového okna rozbalte **projekty a řešení**a potom klikněte na tlačítko **VB výchozí**. Počáteční výchozí nastavení **Option Strict** v **výchozí hodnoty pro VB** je **vypnout**.  
  
  **Možnost Strict jednotlivých upozornění.** **Upozornění konfigurace** část **kompilace stránky** má nastavení, které odpovídají uvedených tří podmínek, které způsobí chybu kompilace při `Option Strict` zapnutý. Tato nastavení jsou následující:  
  
- **Implicitní převod**  
  
- **Pozdní vazba. volání by mohlo selhat v době běhu**  
  
- **Implicitní typ; převzatý objekt**  
  
  Pokud nastavíte **Option Strict** k **na**, všechna tři nastavení konfigurace upozornění jsou nastaveny na **chyba**. Pokud nastavíte **Option Strict** k **vypnout**, všechny tři nastavení **žádný**.  
  
  Samostatně můžete změnit nastavení každé upozornění konfigurace **žádný**, **upozornění**, nebo **chyba**. Pokud mají všechny tři nastavení konfigurace upozornění **chyba**, `On` se zobrazí v `Option strict` pole. Pokud mají všechny tři **žádný**, `Off` se zobrazí v tomto poli. Pro libovolnou kombinaci těchto nastavení **(vlastní)** se zobrazí.  
  
  **Možnost compare**  
  Určuje typ porovnání řetězců k použití. Vyberte **binární** dáte pokyn, aby kompilátor používal porovnávání řetězců binární, velká a malá písmena. Vyberte **Text** použít porovnávání řetězců specifické pro národní prostředí, nerozlišuje velikost písmen textu.  
  
  Toto nastavení odpovídá [/optioncompare](http://msdn.microsoft.com/library/7237b766-b44d-4cc5-9a3c-885348a7d9e4) – možnost kompilátoru.  
  
  Pokud soubor zdrojového kódu obsahuje [možnost porovnat příkaz](http://msdn.microsoft.com/library/54e8eeeb-3b0d-4fb9-acce-fbfbd5975f6e), `Binary` nebo `Text` hodnota v příkazu přepíše **Option Compare** nastavení na **kompilace stránka**.  
  
  Při vytváření projektu, **Option Compare** nastavení **kompilace stránky** je nastavena na hodnotu **Option Compare** nastavení **možnosti** dialogové okno. Chcete-li zobrazit nebo změnit nastavení v tomto dialogovém okně na **nástroje** nabídky, klikněte na tlačítko **možnosti**. V **možnosti** dialogového okna rozbalte **projekty a řešení**a potom klikněte na tlačítko **VB výchozí**. Počáteční výchozí nastavení **Option Compare** v **výchozí hodnoty pro VB** je **binární**.  
  
  **Možnost infer**  
  Určuje, jestli se má povolit odvození místního typu v deklaraci proměnných. Vyberte **na** k povolení použití odvození místního typu. Vyberte **vypnout** k odvození místního typu blok.  
  
  Toto nastavení odpovídá [/optioninfer](http://msdn.microsoft.com/library/f6c09db1-0553-464a-abe3-d4510c61d6ed) – možnost kompilátoru.  
  
  Pokud soubor zdrojového kódu obsahuje [Option Infer – příkaz](http://msdn.microsoft.com/library/4ad3e6e9-8f5b-4209-a248-de22ef6e4652), `On` nebo `Off` hodnota v příkazu přepíše **Option Infer** nastavení **kompilace stránky** .  
  
  Při vytváření projektu, **Option Infer** nastavení **kompilace stránky** je nastavena na hodnotu **Option Infer** nastavení **možnosti**dialogové okno. Chcete-li zobrazit nebo změnit nastavení v tomto dialogovém okně na **nástroje** nabídky, klikněte na tlačítko **možnosti**. V **možnosti** dialogového okna rozbalte **projekty a řešení**a potom klikněte na tlačítko **VB výchozí**. Počáteční výchozí nastavení **Option Infer** v **výchozí hodnoty pro VB** je **na**.  
  
  **Cíl CPU**  
  Určuje procesor, který bude cílen výstupním souborem. Zadejte **x86** pro jakýkoli procesor kompatibilní s verzí Intel 32-bit **x64** pro jakýkoli procesor kompatibilní s verzí Intel 64-bit **ARM** pro jakýkoli procesor ARM nebo **jakýkoli procesor**  k určení, že je přijatelný jakýkoli procesor. **Jakýkoli procesor** je výchozí hodnota pro nové projekty, protože umožňuje aplikaci, aby běžela na největší počet typů hardwaru.  
  
  Další informace najdete v tématu [/Platform (Visual Basic)](http://msdn.microsoft.com/library/f9bc61e6-e854-4ae1-87b9-d6244de23fd1).  
  
  **Preferovat 32 bitů**  
  Pokud **preferovat 32bitovou verzi** zaškrtávací políčko zaškrtnuto, aplikace běží jako 32bitová aplikace ve 32bitové a 64bitové verze Windows. V opačném případě aplikace běží jako 32bitová aplikace ve 32bitové verze Windows a jako na 64bitovými verzemi Windows 64-bit aplikace.  
  
  Spuštění aplikace 64-bit zdvojnásobuje velikost ukazatele, a to může způsobit problémy s kompatibilitou s knihovnami, které jsou výhradně 32bitové. Je vhodné spustit aplikaci jako 64-bit pouze v případě, že je výrazně rychlejší spuštění, nebo potřebuje více než 4 GB paměti.  
  
  Toto zaškrtávací políčko je dostupné jenom v případě, že jsou splněny všechny následující podmínky:  
  
- Na **stránka kompilovat**, **cílový procesor** seznamu je nastavena na **jakýkoli procesor**.  
  
- Na **stránky aplikace**, **typ aplikace** seznam určuje, že projekt je aplikace.  
  
- Na **stránky aplikace**, **Cílová architektura** seznamu určuje rozhraní .NET Framework 4.5.  
  
  **Konfigurace upozornění**  
  Tato tabulka shrnuje sestavení podmínky a odpovídající úroveň oznámení **žádný**, **upozornění**, nebo **chyba** pro každý.  
  
  Ve výchozím nastavení všechna upozornění kompilátoru přidají do seznamu úkolů během kompilace. Vyberte **zakázat všechna upozornění** dáte pokyn kompilátoru, aby problém upozornění a chyby. Vyberte **považovat všechna upozornění jako chyby** Pokud chcete, aby kompilátor zpracovávat upozornění jako chyby, které je potřeba opravit.  
  
  **Zakázat všechna upozornění**  
  Určuje, jestli chce použít kompilátor, aby uvedená v upozornění na problémy **podmínku a oznámení** tabulky popsané dříve v tomto dokumentu. Ve výchozím nastavení je toto políčko zaškrtnuté. Toto políčko zaškrtnuto, abyste instruovali kompilátor není vydat upozornění a chyby.  
  
  Toto nastavení odpovídá [/nowarn](http://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83) – možnost kompilátoru.  
  
  **Považovat všechna upozornění jako chyby**  
  Určuje, jak zpracovávat upozornění. Ve výchozím nastavení, toto zaškrtávací políčko zaškrtnuto, takže všechna upozornění oznámení zůstanou nastavená na **upozornění**. Zaškrtněte toto políčko, chcete-li změnit všechna oznámení upozornění pro **chyba**.  
  
  Tato možnost je dostupná pouze tehdy, pokud **zakázat všechna upozornění** se vymaže.  
  
  **Generovat soubor dokumentace XML**  
  Určuje, jestli se má generovat informace o dokumentaci. Ve výchozím nastavení je toto políčko zaškrtnuto, že kompilátoru generovat informace o dokumentaci a zahrnout do souboru XML. Zrušte zaškrtnutí tohoto políčka, abyste instruovali kompilátor nechcete vytvářet dokumentaci.  
  
  Toto nastavení odpovídá [/doc](http://msdn.microsoft.com/library/5fc32ec9-a149-4648-994c-a8d0cccd0a65) – možnost kompilátoru.  
  
  **Zaregistrovat pro interoperabilitu COM**  
  Určuje, zda bude vaše spravovaná aplikace vystavovat objekt modelu COM (Obálka volatelná aplikacemi COM) umožňující objektu modelu COM interakci s aplikací.  
  
  Ve výchozím nastavení je toto zaškrtávací políčko zaškrtnuto, který určuje, že aplikace nebude umožňovat komunikace s objekty COM. Vyberte toto zaškrtávací políčko pro povolení komunikace s objekty COM.  
  
  Tato možnost není k dispozici pro projekty aplikací pro Windows nebo konzolové aplikace.  
  
  **Události sestavení**  
  Kliknutím na toto tlačítko přístup **události sestavení** dialogové okno. Použijte toto dialogové okno k určení pokyny ke konfiguraci před a po sestavení projektu. Toto dialogové okno se vztahují na projekty Visual Basic pouze. Další informace najdete v tématu [sestavení dialogové okno události (Visual Basic)](../../ide/reference/build-events-dialog-box-visual-basic.md).  
  
  **Možnosti rozšířené kompilace**  
  Kliknutím na toto tlačítko přístup **AdvancedCompiler nastavení** dialogové okno. Použití **AdvancedCompiler nastavení** dialogové okno k zadání projekt rozšířenou vlastností konfigurace sestavení. Toto dialogové okno se vztahují na projekty Visual Basic pouze. Další informace najdete v tématu [Advanced kompilátoru dialogové okno nastavení (Visual Basic)](../../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md).  
  
## <a name="see-also"></a>Viz také  
 [Konfigurace ladění a verzí projektu](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e)   
 [Správa vlastností kompilace](http://msdn.microsoft.com/en-us/94308881-f10f-4caf-a729-f1028e596a2c)   
 [Postupy: určení událostí sestavení (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)   
 [Kompilátor příkazového řádku jazyka Visual Basic](http://msdn.microsoft.com/library/6b57c444-50c7-4b88-8f59-ed65cff5e05c)   
 [Postupy: Vytvoření a úprava konfigurací](../../ide/how-to-create-and-edit-configurations.md)



