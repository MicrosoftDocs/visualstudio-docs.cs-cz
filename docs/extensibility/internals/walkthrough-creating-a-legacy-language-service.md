---
title: 'Návod: vytvoření služby starší verze jazyka | Microsoft Docs'
description: Naučte se používat třídy jazyka Managed Package Framework k implementaci jazykové služby v jazyce Visual C#.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- language services [managed package framework], creating
ms.assetid: 6a5dd2c2-261b-4efd-a3f4-8fb90b73dc82
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 61f4dfd8068cc44fca97eb5e07ddbf62b21ee1f2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899911"
---
# <a name="walkthrough-creating-a-legacy-language-service"></a>Návod: Vytvoření služby starší verze jazyka
Použití tříd jazyka Managed Package Framework (MPF) pro implementaci jazykové služby v nástroji [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] je jednoduché. Pro hostování jazykové služby, samotné služby jazyka a analyzátoru pro váš jazyk potřebujete VSPackage.

## <a name="prerequisites"></a>Požadavky
 Chcete-li postupovat podle tohoto návodu, je nutné nainstalovat sadu Visual Studio SDK. Další informace najdete v tématu [Visual Studio SDK](../../extensibility/visual-studio-sdk.md).

## <a name="locations-for-the-visual-studio-package-project-template"></a>Umístění pro šablonu projektu balíčku sady Visual Studio
 Šablonu projektu balíčku sady Visual Studio najdete ve třech různých umístěních šablon v dialogovém okně **Nový projekt** :

1. V části rozšíření Visual Basic. Výchozí jazyk projektu je Visual Basic.

2. V části rozšiřitelnost jazyka C#. Výchozím jazykem projektu je C#.

3. V rámci rozšíření jiných typů projektů. Výchozí jazyk projektu je C++.

### <a name="create-a-vspackage"></a>Vytvoření balíčku VSPackage

1. Vytvořte nový VSPackage pomocí šablony projektu balíčku sady Visual Studio.

    Pokud přidáváte službu jazyka do existujícího balíčku VSPackage, přeskočte následující kroky a přejděte přímo do části Vytvoření třídy jazykové služby.

2. Jako název projektu zadejte MyLanguagePackage a klikněte na **OK**.

    Můžete použít libovolný požadovaný název. Zde popsané postupy předpokládají jako název MyLanguagePackage.

3. Vyberte [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] jako jazyk a možnost pro vygenerování nového souboru klíče. Klikněte na **Next** (Další).

4. Zadejte příslušné informace o společnosti a balíčku. Klikněte na **Next** (Další).

5. Vyberte **příkaz nabídky**. Klikněte na **Next** (Další).

    Pokud nechcete podporovat fragmenty kódu, můžete pouze kliknout na tlačítko Dokončit a ignorovat další krok.

6. Jako **název příkazu** zadejte **Vložit fragment** a `cmdidInsertSnippet` pro **ID příkazu**. Klikněte na **Finish** (Dokončit).

    **Název příkazu** a **ID příkazu** můžou být libovolné, co chcete, ale ty jsou jenom příklady.

### <a name="create-the-language-service-class"></a>Vytvoření třídy jazykové služby

1. V **Průzkumník řešení** klikněte pravým tlačítkem myši na projekt MyLanguagePackage, zvolte možnost **Přidat**, **odkaz** a pak klikněte na tlačítko **Přidat nový odkaz** .

2. V dialogovém okně **Přidat odkaz** vyberte na kartě **.NET** možnost **Microsoft. VisualStudio. Package. LanguageService** a klikněte na tlačítko **OK**.

     To je nutné provést pouze jednou pro projekt jazykové balíčky.

3. V **Průzkumník řešení** klikněte pravým tlačítkem na projekt VSPackage a vyberte **Přidat**, **Třída**.

4. Ujistěte se, že je v seznamu šablon vybrána možnost **Třída** .

5. Jako název souboru třídy zadejte **MyLanguageService.cs** a klikněte na **Přidat**.

     Můžete použít libovolný požadovaný název. Tyto postupy popsané tady předpokládají `MyLanguageService` jako název.

6. Do souboru MyLanguageService.cs přidejte následující `using` direktivy.

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_1.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_1.vb)]

7. Upravte `MyLanguageService` třídu pro odvození z <xref:Microsoft.VisualStudio.Package.LanguageService> třídy:

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_2.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_2.vb)]

8. Umístěte kurzor na "LanguageService" a v nabídce **Úpravy**, **technologie IntelliSense** vyberte **implementovat abstraktní třídu**. Tím se přidají minimální nezbytné metody pro implementaci třídy jazykové služby.

9. Implementujte abstraktní metody, jak je popsáno v tématu [implementace starší verze jazykové služby](../../extensibility/internals/implementing-a-legacy-language-service2.md).

### <a name="register-the-language-service"></a>Registrace jazykové služby

1. Otevřete soubor MyLanguagePackagePackage.cs a přidejte následující `using` direktivy:

     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_3.vb)]
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_3.cs)]

2. Zaregistrujte třídu služby jazyka, jak je popsáno v tématu [Registrace služby starší verze jazyka](../../extensibility/internals/registering-a-legacy-language-service1.md). Patří sem atributy ProvideXX a Proffering části služby jazyka. Použijte MyLanguageService, kde toto téma používá TestLanguageService.

### <a name="the-parser-and-scanner"></a>Analyzátor a skener

1. Implementujte analyzátor a skener pro svůj jazyk, jak je popsáno v tématu [analyzátor a skener služby starší verze jazyka](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).

     Způsob implementace analyzátoru a skener je zcela na vás a je nad rámec tohoto tématu.

## <a name="language-service-features"></a>Funkce služby jazyka
 Chcete-li implementovat jednotlivé funkce v jazykové službě, obvykle je odvozena třída z příslušné třídy služby jazyka MPF, implementujte všechny abstraktní metody podle potřeby a přepište vhodné metody. Třídy, které vytvoříte nebo odvozuje, jsou závislé na funkcích, které chcete podporovat. Tyto funkce jsou podrobně popsány v tématu [funkce služby starší verze jazyka](../../extensibility/internals/legacy-language-service-features1.md). Následující postup je obecný přístup k odvození třídy z třídy MPF.

#### <a name="deriving-from-an-mpf-class"></a>Odvození z třídy MPF

1. V **Průzkumník řešení** klikněte pravým tlačítkem na projekt VSPackage a vyberte **Přidat**, **Třída**.

2. Ujistěte se, že je v seznamu šablon vybrána možnost **Třída** .

     Zadejte vhodný název pro soubor třídy a klikněte na **Přidat**.

3. V novém souboru třídy přidejte následující `using` direktivy.

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_4.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_4.vb)]

4. Upravte třídu tak, aby byla odvozena z požadované třídy MPF.

5. Přidejte konstruktor třídy, který přebírá alespoň stejné parametry jako konstruktor základní třídy a předá parametry konstruktoru konstruktoru základní třídy.

     Například konstruktor pro třídu odvozenou z <xref:Microsoft.VisualStudio.Package.Source> třídy může vypadat takto:

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_5.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_5.vb)]

6. V nabídce **Úpravy**, **technologie IntelliSense** vyberte **implementovat abstraktní třídu** , pokud má základní třída jakékoli abstraktní metody, které musí být implementovány.

7. V opačném případě umístěte blikající kurzor dovnitř třídy a zadejte metodu, která má být přepsána.

     Například zadejte, `public override` Chcete-li zobrazit seznam všech metod, které lze v této třídě přepsat.

## <a name="see-also"></a>Viz také
- [Implementace služby starší verze jazyka](../../extensibility/internals/implementing-a-legacy-language-service1.md)
