---
title: 'Návod: Vytvoření služby staršíverze jazyka | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], creating
ms.assetid: 6a5dd2c2-261b-4efd-a3f4-8fb90b73dc82
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 59ec18ab0c97ec89422e06f5b33804adcc750d5a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703689"
---
# <a name="walkthrough-creating-a-legacy-language-service"></a>Návod: Vytvoření služby starší verze jazyka
Použití jazykových tříd rozhraní Spravovaného balíčku [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] (MPF) k implementaci jazykové služby v jazyce je jednoduché. Potřebujete VSPackage pro hostování jazykové služby, samotné jazykové služby a analyzátoru pro váš jazyk.

## <a name="prerequisites"></a>Požadavky
 Chcete-li postupovat podle tohoto návodu, je nutné nainstalovat sady Visual Studio SDK. Další informace naleznete v [tématu Visual Studio SDK](../../extensibility/visual-studio-sdk.md).

## <a name="locations-for-the-visual-studio-package-project-template"></a>Umístění pro šablonu projektu balíčku sady Visual Studio
 Šablonu projektu balíčku sady Visual Studio najdete ve třech různých umístěních šablon v dialogovém okně **Nový projekt:**

1. V části Rozšiřitelnost jazyka. Výchozí jazyk projektu je Visual Basic.

2. Pod C# Rozšiřitelnost. Výchozí jazyk projektu je C#.

3. V části Jiné typy projektů Rozšiřitelnost. Výchozí jazyk projektu je C++.

### <a name="create-a-vspackage"></a>Vytvoření balíčku VSPackage

1. Vytvořte nový Balíček VSPackage se šablonou projektu balíček Sady Visual Studio.

    Pokud přidáváte jazykovou službu do existujícího balíčku VSPackage, přeskočte následující kroky a přejděte přímo k postupu "Vytvořit třídu jazykové služby".

2. Zadejte MyLanguagePackage pro název projektu a klepněte na tlačítko **OK**.

    Můžeš použít jakékoliv jméno. Tyto postupy podrobně zde převzít MyLanguagePackage jako název.

3. Vyberte [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] jako jazyk a možnost generovat nový soubor klíče. Klikněte na **Další**.

4. Zadejte příslušné informace o společnosti a balíčku. Klikněte na **Další**.

5. Vyberte **příkaz nabídky**. Klikněte na **Další**.

    Pokud nemáte v úmyslu podporovat fragmenty kódu, stačí kliknout na dokončit a ignorovat další krok.

6. Zadejte **Vložit úryvek** jako `cmdidInsertSnippet` název **příkazu** a pro **ID příkazu**. Klikněte na **Finish** (Dokončit).

    **Název příkazu** a **ID příkazu** může být, co chcete, to jsou jen příklady.

### <a name="create-the-language-service-class"></a>Vytvoření třídy jazykové služby

1. V **Průzkumníku řešení**klikněte pravým tlačítkem myši na projekt MyLanguagePackage, zvolte **Přidat**, **Reference**a pak zvolte tlačítko Přidat **nový odkaz.**

2. V dialogovém okně **Přidat odkaz** vyberte na kartě **.NET** službu **Microsoft.VisualStudio.Package.LanguageService** a klepněte na tlačítko **OK**.

     To je třeba provést pouze jednou pro projekt jazykového balíčku.

3. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt VSPackage a vyberte **přidat** **položku Class**.

4. Ujistěte se, že je v seznamu šablon vybraná možnost **Třída.**

5. Zadejte **MyLanguageService.cs** pro název souboru třídy a klepněte na **tlačítko Přidat**.

     Můžeš použít jakékoliv jméno. Tyto postupy zde `MyLanguageService` podrobně předpokládají jako název.

6. Do MyLanguageService.cs souboru přidejte následující `using` direktivy.

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_1.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_1.vb)]

7. Upravte `MyLanguageService` třídu, <xref:Microsoft.VisualStudio.Package.LanguageService> která má být odvozena z třídy:

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_2.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_2.vb)]

8. Umístěte kurzor na "LanguageService" a z nabídky **Upravit**, **IntelliSense** vyberte **Implementovat abstraktní třídu**. Tím se přidá minimální nezbytné metody k implementaci třídy služby jazyka.

9. Implementujte abstraktní metody popsané v [části Implementace služby staršího jazyka](../../extensibility/internals/implementing-a-legacy-language-service2.md).

### <a name="register-the-language-service"></a>Registrace jazykové služby

1. Otevřete soubor MyLanguagePackagePackage.cs a `using` přidejte následující direktivy:

     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_3.vb)]
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_3.cs)]

2. Zaregistrujte svou třídu jazykových služeb, jak je popsáno v [seznamu Registrace služby staršího jazyka](../../extensibility/internals/registering-a-legacy-language-service1.md). To zahrnuje atributy ProvideXX a části "Proffering the Language Service". Použijte MyLanguageService, kde toto téma používá TestLanguageService.

### <a name="the-parser-and-scanner"></a>Analyzátor a skener

1. Implementujte analyzátor a skener pro váš jazyk, jak je popsáno v [analyzátoru a skeneru starších jazykových služeb](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).

     Jak implementovat analyzátor a skener je zcela na vás a je nad rámec tohoto tématu.

## <a name="language-service-features"></a>Funkce jazykové služby
 Chcete-li implementovat každou funkci ve službě jazyka, obvykle odvodit třídu z příslušné třídy služby jazyka MPF, implementovat všechny abstraktní metody podle potřeby a přepsat příslušné metody. Třídy, které vytvoříte nebo odvodíte, závisí na funkcích, které chcete podporovat. Tyto funkce jsou podrobně popsány v [funkcích služby Starší jazyk .](../../extensibility/internals/legacy-language-service-features1.md) Následující postup je obecný přístup k odvození třídy z Třídy MPF.

#### <a name="deriving-from-an-mpf-class"></a>Odvození ze třídy MPF

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt VSPackage a vyberte **přidat** **položku Class**.

2. Ujistěte se, že je v seznamu šablon vybraná možnost **Třída.**

     Zadejte vhodný název souboru třídy a klepněte na **tlačítko Přidat**.

3. Do nového souboru třídy přidejte následující `using` direktivy.

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_4.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_4.vb)]

4. Upravte třídu tak, aby byla odvozena z požadované třídy MPF.

5. Přidejte konstruktor třídy, který má alespoň stejné parametry jako konstruktor základní třídy a předá parametry konstruktoru do konstruktoru základní třídy.

     Například konstruktor pro třídu odvozenou <xref:Microsoft.VisualStudio.Package.Source> z třídy může vypadat takto:

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_5.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_5.vb)]

6. V nabídce **Edit**, **IntelliSense** vyberte **Implementovat abstraktní třídu,** pokud základní třída obsahuje všechny abstraktní metody, které musí být implementovány.

7. V opačném případě umístěte stříšku uvnitř třídy a zadejte metodu, která má být přepsána.

     Zadejte `public override` například seznam všech metod, které mohou být v této třídě přepsány.

## <a name="see-also"></a>Viz také
- [Implementace služby starší verze jazyka](../../extensibility/internals/implementing-a-legacy-language-service1.md)
