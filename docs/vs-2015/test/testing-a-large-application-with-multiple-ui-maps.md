---
title: Testování rozsáhlé aplikace s více mapami uživatelského rozhraní | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- coded UI tests, multiple UI maps
- coded UI tests, for large applications
ms.assetid: 6e1ae9ec-e9b1-458a-bd96-0eb15e46f1d5
caps.latest.revision: 24
ms.author: gewarren
manager: douge
ms.openlocfilehash: 0bc13aa389d6597831682cad62bcaad53672fa7b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49893464"
---
# <a name="testing-a-large-application-with-multiple-ui-maps"></a>Testování rozsáhlé aplikace s více mapami uživatelského rozhraní
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma popisuje, jak používat programové testy UI při testování rozsáhlé aplikace s použitím více mapami uživatelského rozhraní.  
  
 **Požadavky**  
  
- Visual Studio Enterprise  
  
  Při vytváření nového programového testu uživatelského rozhraní, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] testovací rozhraní generuje kód testu ve výchozím nastavení <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> třídy. Další informace o tom, jak zaznamenat programové testy UI, naleznete v tématu [vytváření programových testů UI](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate) a [anatomie programového testu UI](../test/anatomy-of-a-coded-ui-test.md).  
  
  Generovaný kód pro mapování uživatelského rozhraní obsahuje třídu pro každý objekt, který komunikuje testu. Pro jednotlivé metody generované třídě doprovodných prvků pro parametry metody je vygenerován speciálně pro tuto metodu. Pokud existuje velký počet objektů, stránek, formuláře a ovládací prvky v aplikaci, můžou růst velmi velké mapování uživatelského rozhraní. Navíc pokud několik lidí pracují na testy, aplikace nepraktický s jeden velký soubor mapování uživatelského rozhraní.  
  
  Použití více souborů mapování uživatelského rozhraní může poskytnout následující výhody:  
  
- Každé mapování můžou být spojené s podmnožinu logické aplikace. To usnadňuje změny pro správu.  
  
- Každý tester můžete pracovat v části aplikace a zkontrolujte ve svém kódu, aniž by zasahovala do jiných testery pracující na ostatní části aplikace.  
  
- Doplňky uživatelského rozhraní aplikace je možné škálovat postupně s minimálním vlivem na testy jiné části uživatelského rozhraní.  
  
## <a name="do-you-need-multiple-ui-maps"></a>Potřebujete více mapami uživatelského rozhraní?  
 Vytvoření více mapami uživatelského rozhraní v každém z těchto typů situacích:  
  
-   Několik sad komplexní složených ovládacích prvků uživatelského rozhraní, které dohromady provádějí logické operace, jako je například na registrační stránce na webu nebo na stránce nákupní nákupního košíku.  
  
-   Nezávislého sadu ovládacích prvků, které jsou přístupné z různých míst aplikaci, jako je průvodce se několik stránek operací. Pokud je obzvláště složité každou stránku průvodce, můžete vytvořit samostatné mapami uživatelského rozhraní pro každou stránku.  
  
## <a name="adding-multiple-ui-maps"></a>Přidání více mapami uživatelského rozhraní  
  
#### <a name="to-add-a-ui-map-to-your-coded-ui-test-project"></a>Chcete-li přidat mapování uživatelského rozhraní pro váš projekt programového testu UI  
  
1. V **Průzkumníka řešení**, abyste vytvořili složku v váš projekt programového testu UI pro uložení všech mapami uživatelského rozhraní, klikněte pravým tlačítkem na souboru projektu programového testu uživatelského rozhraní, přejděte na **přidat** a klikněte na tlačítko **novou složku**. Třeba mohla mít název `UIMaps`.  
  
    Nové složky se zobrazí v části Projekt programového testu UI.  
  
2. Klikněte pravým tlačítkem myši `UIMaps` složku, přejděte na příkaz **přidat**a klikněte na tlačítko **nová položka**.  
  
    **Přidat novou položku** se zobrazí dialogové okno.  
  
   > [!NOTE]
   >  Musí být v projektu programového testu UI přidat nové mapování programového testu uživatelského rozhraní.  
  
3. Vyberte **programový Test mapování uživatelského rozhraní** ze seznamu.  
  
    V **název** pole, zadejte název nové mapování uživatelského rozhraní. Použijte název komponenty nebo stránka, která bude představovat mapy, například `HomePageMap`.  
  
4. Zvolte **přidat**.  
  
    [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Minimalizuje okno a **Tvůrce programového testu UI** se zobrazí dialogové okno.  
  
5. Záznam akce pro metodu první a zvolte **generovat kód**.  
  
6. Po zaznamenané všechny akce a kontrolní výrazy pro první komponenta nebo stránky a seskupeny do metod, zavřete **Tvůrce programového testu UI** dialogové okno.  
  
7. Pokračujte ve vytváření mapami uživatelského rozhraní. Záznam akce a kontrolní výrazy, seskupte je do metod pro každou komponentu a potom generovat kód.  
  
   V mnoha případech okna nejvyšší úrovně vaší aplikace zůstává konstantní průvodců, formulářů a stránky. I když každá mapování uživatelského rozhraní obsahuje třídu pro okna nejvyšší úrovně, jsou všechny mapy pravděpodobně odkazující na stejné okno nejvyšší úrovně v rámci které všechny součásti aplikace spouštět. Programového uživatelského rozhraní testy hledání pro ovládací prvky hierarchicky shora dolů, z okna na nejvyšší úrovni tak komplexní aplikace, může být duplicitní okně skutečné nejvyšší úrovně v každé mapování uživatelského rozhraní. Pokud okno skutečné nejvyšší úrovně je duplicitní, víc úpravy dojde, pokud se toto okno změní. To může způsobit problémy s výkonem při přepínání mezi mapami uživatelského rozhraní.  
  
   Chcete-li minimalizovat tento efekt, můžete použít `CopyFrom()` metoda zajistit, aby nové okno nejvyšší úrovně v tom, že mapování uživatelského rozhraní je stejný jako hlavní okno nejvyšší úrovně.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu je součástí nástroje třídu, která poskytuje přístup k jednotlivé komponenty a jejich podřízené ovládací prvky, které jsou znázorněny prostor tříd vygenerovaných v různých mapami uživatelského rozhraní.  
  
 V tomto příkladu webovou aplikaci s názvem `Contoso` má Domovská stránka, na stránce produktu a stránku nákupní košík. Každá z těchto stránek sdílejí společné okno nejvyšší úrovně, což je okno prohlížeče. Existuje mapování uživatelského rozhraní pro každou stránku a utility třída má kód podobný následujícímu:  
  
```  
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
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.BrowserWindow.CopyFrom%2A>   
 [Použití automatizace uživatelského rozhraní k testování kódu](../test/use-ui-automation-to-test-your-code.md)   
 [Vytváření programových testů UI](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)   
 [Anatomie programového testu UI](../test/anatomy-of-a-coded-ui-test.md)



