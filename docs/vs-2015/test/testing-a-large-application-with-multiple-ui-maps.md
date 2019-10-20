---
title: Testování rozsáhlé aplikace s více mapami uživatelského rozhraní | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, multiple UI maps
- coded UI tests, for large applications
ms.assetid: 6e1ae9ec-e9b1-458a-bd96-0eb15e46f1d5
caps.latest.revision: 24
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2f6936811ea753d66d212facdda627930fb1ab10
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672129"
---
# <a name="testing-a-large-application-with-multiple-ui-maps"></a>Testování rozsáhlé aplikace s více mapami uživatelského rozhraní
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma popisuje, jak používat kódované testy uživatelského rozhraní při testování rozsáhlých aplikací pomocí více mapování uživatelského rozhraní.

 **Požadavky**

- Visual Studio Enterprise

  Při vytváření nového programového testu uživatelského rozhraní generuje [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] testovacího prostředí ve výchozím nastavení ve třídě [UIMap](/previous-versions/dd580454(v=vs.140)) kód pro test. Další informace o tom, jak zaznamenat programové testy UI, naleznete v tématu vytváření programových [testů uživatelského rozhraní](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate) a [anatomie programového testu uživatelského rozhraní](../test/anatomy-of-a-coded-ui-test.md).

  Generovaný kód pro mapu uživatelského rozhraní obsahuje třídu pro každý objekt, se kterým pracuje test. Pro každou vygenerovanou metodu je doprovodná třída pro parametry metody generována speciálně pro tuto metodu. Pokud je ve vaší aplikaci velký počet objektů, stránek a formulářů a ovládacích prvků, mapa uživatelského rozhraní se může zvětšovat velmi veliké. Pokud na testech pracuje více lidí, aplikace se bude nepraktický s jedním velkým souborem mapování uživatelského rozhraní.

  Používání více souborů mapa uživatelského rozhraní může mít následující výhody:

- Každá mapa může být přidružena k logické podmnožině aplikace. To usnadňuje správu změn.

- Každý tester může pracovat na oddílu aplikace a vrátit se změnami kód bez rušivého vlivu na jiné testery aplikace.

- Doplňování uživatelského rozhraní aplikace lze škálovat přírůstkově s minimálním dopadem na testy pro jiné části uživatelského rozhraní.

## <a name="do-you-need-multiple-ui-maps"></a>Potřebujete několik mapování uživatelského rozhraní?
 Vytvoření více mapování uživatelského rozhraní v každém z těchto typů situací:

- Několik komplexních sad složených ovládacích prvků uživatelského rozhraní, které společně provádějí logickou operaci, jako například registrační stránku na webu nebo na stránce nákup nákupního košíku.

- Nezávislá sada ovládacích prvků, které jsou k dispozici z různých bodů aplikace, jako je například Průvodce s několika stránkami operací. Pokud je každá stránka průvodce zvlášť složitá, můžete pro každou stránku vytvořit samostatná mapování uživatelského rozhraní.

## <a name="adding-multiple-ui-maps"></a>Přidání více mapování uživatelského rozhraní

#### <a name="to-add-a-ui-map-to-your-coded-ui-test-project"></a>Chcete-li přidat mapu uživatelského rozhraní do projektu programového testu uživatelského rozhraní

1. V **Průzkumník řešení**pro vytvoření složky v projektu programového testu uživatelského rozhraní pro uložení všech map uživatelského rozhraní, klikněte pravým tlačítkem na soubor projektu programového testu UI, přejděte na **Přidat** a pak zvolte **Nová složka**. Můžete ho například pojmenovat `UIMaps`.

    Nová složka se zobrazí v rámci projektu programového testu uživatelského rozhraní.

2. Klikněte pravým tlačítkem na složku `UIMaps`, přejděte na **Přidat**a pak zvolte **Nová položka**.

    Zobrazí se dialogové okno **Přidat novou položku** .

   > [!NOTE]
   > Chcete-li přidat novou mapu programového testu UI, musíte být v projektu programového testu uživatelského rozhraní.

3. Ze seznamu vyberte mapa programového **testu uživatelského rozhraní** .

    Do pole **název** zadejte název nového mapování uživatelského rozhraní. Použijte název součásti nebo stránky, kterou bude mapa představovat, například `HomePageMap`.

4. Klikněte na tlačítko **Přidat**.

    Okno [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] minimalizuje a zobrazí se dialogové okno Tvůrce programového **testu uživatelského rozhraní** .

5. Zaznamenejte akce pro první metodu a vyberte možnost **generovat kód**.

6. Po zaznamenání všech akcí a kontrolních výrazů pro první komponentu nebo stránku a jejich seskupení do metod zavřete dialogové okno Tvůrce programového **testu uživatelského rozhraní** .

7. Pokračujte v vytváření map uživatelského rozhraní. Zaznamenejte akce a kontrolní výrazy, seskupte je do metod pro každou komponentu a potom kód vygenerujte.

   V mnoha případech zůstane okno aplikace nejvyšší úrovně pro všechny průvodce, formuláře a stránky konstantní. Přestože má každé mapování uživatelského rozhraní třídu pro okno nejvyšší úrovně, všechny mapy se pravděpodobně odkazují na stejné okno nejvyšší úrovně, ve kterém jsou spuštěny všechny komponenty aplikace. Programové testy uživatelského rozhraní hledají ovládací prvky hierarchicky shora dolů, počínaje z okna nejvyšší úrovně, takže ve složitých aplikacích může být okno reálné nejvyšší úrovně duplicitní v každé mapě uživatelského rozhraní. Pokud je okno nejvyšší nejvyšší úrovně duplicitní, bude výsledkem více úprav, pokud se změní toto okno. To může způsobit problémy s výkonem při přepínání mezi mapami uživatelského rozhraní.

   K minimalizaci tohoto efektu můžete použít metodu `CopyFrom()` k zajištění toho, aby nové okno nejvyšší úrovně v této mapě uživatelského rozhraní bylo stejné jako hlavní okno nejvyšší úrovně.

## <a name="example"></a>Příklad
 Následující příklad je součástí třídy nástrojů, která poskytuje přístup k jednotlivým komponentám a jejich podřízeným ovládacím prvkům, které jsou reprezentovány třídami vygenerovanými v různých mapách uživatelského rozhraní.

 V tomto příkladu webová aplikace s názvem `Contoso` má domovskou stránku, stránku produktu a na stránku nákupního košíku. Každá z těchto stránek sdílí společné okno nejvyšší úrovně, které je oknem prohlížeče. K dispozici je mapa uživatelského rozhraní pro každou stránku a třída utility má kód podobný následujícímu:

```csharp
using ContosoProject.UIMaps;
using ContosoProject.UIMaps.HomePageClasses;
using ContosoProject.UIMaps.ProductPageClasses;
using ContosoProject.UIMaps.ShoppingCartClasses;

namespace ContosoProject
{
    public class TestRunUtility
    {
        // Private fields for the properties
        private HomePage homePage = null;
        private ProductPage productPage = null;
        private ShoppingCart shoppingCart = null;

        public TestRunUtility()
        {
            homePage = new HomePage();
        }

        // Properties that get each UI Map
        public HomePage HomePage
        {
            get { return homePage; }
            set { homePage = value; }
        }

        // Gets the ProductPage from the ProductPageMap.
        public ProductPage ProductPageObject
        {
            get
            {
                if (productPage == null)
                {
                    // Instantiate a new page from the UI Map classes
                    productPage = new ProductPage();

                    // Since the Product Page and Home Page both use
                    // the same browser page as the top level window,
                    // get the top level window properties from the
                    // Home Page.
                    productPage.UIContosoFinalizeWindow.CopyFrom(
                        HomePage.UIContosoWindowsIWindow);
                }
                return productPage;
            }
        }

    // Continue to create properties for each page, getting the
    // page object from the corresponding UI Map and copying the
    // top level window properties from the Home Page.
}
```

## <a name="see-also"></a>Viz také:

- [UIMap](/previous-versions/dd580454(v=vs.140))
- <xref:Microsoft.VisualStudio.TestTools.UITesting.BrowserWindow.CopyFrom%2A>
- [Použití automatizace uživatelského rozhraní k testování kódu](../test/use-ui-automation-to-test-your-code.md)
- [Vytváření programových testů uživatelského rozhraní](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)
- [Anatomie programového testu UI](../test/anatomy-of-a-coded-ui-test.md)
