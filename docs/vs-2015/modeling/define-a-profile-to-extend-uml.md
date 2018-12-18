---
title: Definování profilu pro rozšíření UML | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- profiles, UML
- stereotypes, UML
- UML, profiles and stereotypes
- UML - extending, defining profiles
- UML, customizing
- UML, profiles
ms.assetid: 776589cb-f89d-48d5-aafa-04a4c074b0d6
caps.latest.revision: 44
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 37c4560b767828be0ec43419ff92ec5b6f9863ea
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51730330"
---
# <a name="define-a-profile-to-extend-uml"></a>Definování profilu pro rozšíření UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete definovat *profilu UML* k přizpůsobení prvků standardního modelu pro konkrétní účely. Profil definuje jeden nebo více *stereotypů UML*. Stereotyp lze použít k označení typu jako určitého druhu objektu. Stereotyp můžete také rozšířit prvku seznamu vlastností.  
  
 Několik profilů se nainstaluje pomocí podporované edice sady Visual Studio. Tuto funkci podporovat kterou verzí sady Visual Studio najdete v tématu [podporované verze pro nástroje architektury a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport). Další informace o těchto profilech a o tom, jak použít Stereotypy, viz [přizpůsobení modelu pomocí profilů a stereotypů](../modeling/customize-your-model-with-profiles-and-stereotypes.md).  
  
 Můžete definovat vlastní profily k přizpůsobení a rozšíření UML na vlastní obchodní oblast nebo architekturu. Příklad:  
  
- Pokud často definujete webové stránky, můžete definovat vlastní profil, který obsahuje stereotyp "Webové stránky", který lze použít na třídy v diagramech tříd. Může pak použít diagramy tříd k plánování webu. Každá třída «Webová stránka» by měla další vlastnosti pro obsah stránky, styl a tak dále.  
  
- Pokud vyvíjíte bankovní software, můžete definovat profil, který poskytuje stereotyp "Účet". Může pak použít diagramy tříd k definování různých typů účtu a zobrazení vztahů mezi nimi.  
  
  Ke svému týmu můžete distribuovat vlastní profily. Každý člen týmu může nainstalovat váš profil. Díky tomu mohou upravovat a vytvářet modely, které používají jeho stereotypy.  
  
> [!NOTE]
>  Pokud aplikujete Stereotypy profilu v modelu, že upravujete a pak model sdílíte s ostatními lidmi, se musí ve svých počítačích instalovat stejný profil. V opačném případě nebudou moci zobrazit Stereotypy, které jste už použili.  
  
 Profil je často součástí většího [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] rozšíření. Můžete například definovat příkaz, který převede některé části modelu na kód. Můžete definovat profil, který uživatelé musí použít na balíčky, které chtějí překládat. Budete distribuovat váš nový příkaz spolu s profilem v jednom [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] rozšíření.  
  
 Můžete také definovat lokalizované varianty profilu. Uživatelé načítající vaše rozšíření uvidí variantu, která je vhodná pro jejich vlastní jazykovou verzi.  
  
##  <a name="DefineProfile"></a> Jak definovat profil  
  
#### <a name="to-define-a-uml-profile"></a>Definování profilu UML  
  
1.  Vytvořte nový soubor XML s příponou názvu souboru `.profile`.  
  
2.  Přidání definic stereotypu podle pokynů popsaných v [struktura profilu](#Schema).  
  
3.  Přidat profil do rozšíření aplikace Visual Studio (`.vsix` souboru). Můžete vytvořit nové rozšíření pro váš profil nebo profil přidat do existujícího rozšíření.  
  
     Viz následující část [tom, jak přidat profil do rozšíření aplikace Visual Studio](#AddProfile).  
  
4.  Nainstalujte rozšíření ve vašem počítači.  
  
    1.  Dvakrát klikněte na příponu souboru, který má příponu názvu souboru `.vsix`.  
  
    2.  Restartujte sadu Visual Studio.  
  
5.  Ověřte, že profil byl nainstalován.  
  
    1.  V Průzkumníku UML vyberte model.  
  
    2.  V okně Vlastnosti klikněte na tlačítko **profily** vlastnost. Váš profil se zobrazí v nabídce. Nastavte zaškrtávací políčko vedle profilu.  
  
    3.  Vyberte prvek, pro které váš profil definuje stereotypy. V okně Vlastnosti klikněte na tlačítko **Stereotypy** vlastnost. V seznamu se zobrazí vaše stereotypy. Nastavte zaškrtávací políčko proti jednomu stereotypu.  
  
    4.  Pokud váš profil definuje další vlastnosti tohoto stereotypu, rozbalte vlastnosti stereotypu a zobrazte je.  
  
6.  Odešlete soubor rozšíření ostatním uživatelům [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] do svých počítačů nainstalují.  
  
##  <a name="AddProfile"></a> Jak přidat profil do rozšíření aplikace Visual Studio  
 Chcete-li nainstalovat profil a umožnit si odesílat ho jiným uživatelům, musíte přidat profil do rozšíření aplikace Visual Studio. Další informace najdete v tématu [nasazení rozšíření sady Visual Studio](http://go.microsoft.com/fwlink/?LinkId=160780).  
  
#### <a name="to-define-a-profile-in-a-new-visual-studio-extension"></a>Definování profilu v nové rozšíření aplikace Visual Studio  
  
1. Vytvořte projekt rozšíření aplikace Visual Studio.  
  
   > [!NOTE]
   >  Je třeba mít nainstalovanou [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] k použití tohoto postupu.  
  
   1.  Na **souboru** nabídky, přejděte k **nový**a potom klikněte na tlačítko **projektu**.  
  
   2.  V **nový projekt** dialogovém okně **nainstalované šablony**, rozbalte **Visual C#**, klikněte na tlačítko **rozšiřitelnost**a potom klikněte na tlačítko  **Projekt VSIX**. Název projektu a klikněte na tlačítko **OK**.  
  
2. Přidejte profil do projektu.  
  
   -   V Průzkumníku řešení klikněte pravým tlačítkem na projekt, přejděte na **přidat**a potom klikněte na tlačítko **existující položku**. V dialogovém okně vyhledejte soubor profilu.  
  
3. Nastavte soubor profilu **kopírovat do výstupního** vlastnost.  
  
   1.  V Průzkumníku řešení klikněte pravým tlačítkem myši na soubor profilu a potom klikněte na tlačítko **vlastnosti**.  
  
   2.  V okně Vlastnosti nastavte **kopírovat do výstupního adresáře** vlastnost **vždy Kopírovat**.  
  
4. V Průzkumníku řešení otevřete `source.extension.vsixmanifest`.  
  
    Soubor se otevře v editoru manifestu rozšíření.  
  
5. Na **prostředky** stránce, přidejte řádek s popisem profilu:  
  
   -   Klikněte na tlačítko **nové**. Nastavte pole v **přidat nové aktivum** dialogové okno následujícím způsobem.  
  
   -   Nastavte **typ** do `Microsoft.VisualStudio.UmlProfile`  
  
        To však není jednou z možností rozevíracího seznamu. Tento název zadejte z klávesnice.  
  
   -   Klikněte na tlačítko **soubor v systému souborů** a vyberte název souboru profilu, například `MyProfile.profile`  
  
6. Sestavte projekt.  
  
7. **Chcete-li ladit tento profil**, stiskněte klávesu F5.  
  
    Otevře se experimentální instanci sady Visual Studio. V tomto případě otevřete projekt modelování. V Průzkumníku UML vyberte kořenový prvek modelu a v okně Vlastnosti, vyberte svůj profil. Potom vyberte prvky uvnitř modelu a nastavte Stereotypy, které jste pro ně definována.  
  
8. **Extrahování VSIX pro nasazení**  
  
   1.  V Průzkumníku Windows otevřete složku **.\bin\Debug** nebo **.\bin\Release** najít **VSIX** souboru. Jedná se [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] souboru rozšíření. Může být nainstalován v počítači a odeslán ostatním uživatelům aplikace Visual Studio.  
  
   2.  Chcete-li nainstalovat rozšíření:  
  
       1.  Dvakrát klikněte `.vsix` souboru. Instalační služba rozšíření Visual Studio se spustí.  
  
       2.  Restartujte všechny instance sady Visual Studio, na kterých běží.  
  
   Následující alternativní postup lze použít pro malá rozšíření, pokud jste nenainstalovali [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)].  
  
#### <a name="to-define-a-profile-extension-without-using-visual-studio-sdk"></a>Definování rozšíření profilu bez použití Visual Studio SDK  
  
1.  Vytvořte adresář Windows, který obsahuje následující tři soubory:  
  
    -   *YourProfile* `.profile`  
  
    -   `extension.vsixmanifest`  
  
    -   `[Content_Types].xml` -Zadejte tento název, jak je znázorněno zde, v hranatých závorkách  
  
2.  Upravit `[Content_Types].xml` tak, aby obsahovala následující text. Všimněte si, že obsahuje položku pro každou příponu názvu souboru.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <Types xmlns="http://schemas.openxmlformats.org/package/2006/content-types">  
      <Default Extension="profile" ContentType="application/octet-stream" />  
      <Default Extension="vsixmanifest" ContentType="text/xml" />  
    </Types>  
    ```  
  
3.  Kopírovat existující `extension.vsixmanifest` a upravovat pomocí editoru XML. Změnit ID, název a uzlů obsahu.  
  
    -   Příklad najdete `extension.vsixmanifest` v tomto adresáři:  
  
         *jednotky* **: \Program Files\Microsoft \Common7\IDE\Extensions\Microsoft\Architecture Tools\UmlProfiles sady Visual Studio [verze]**  
  
    -   Uzel obsah by měl být takto:  
  
        ```  
        <Content>  
          <CustomExtension Type="Microsoft.VisualStudio.UmlProfile"  
          >YourProfile.Profile</CustomExtension>  
        </Content>  
        ```  
  
4.  Tři soubory zkomprimujte do souboru ZIP.  
  
     V Průzkumníku Windows vyberte tři soubory, klikněte pravým tlačítkem, přejděte na **odeslat**a potom klikněte na tlačítko **komprimovanou složku (ZIP)**.  
  
5.  Přejmenujte zabalený soubory a změňte jeho příponu názvu souboru z `.zip` k `.vsix`.  
  
6.  Profil nainstalovat na libovolném počítači s odpovídajícími verzemi sady Visual Studio, poklepejte `.vsix` souboru.  
  
#### <a name="to-install-a-uml-profile-from-a-visual-studio-extension"></a>Instalace profilu UML z rozšíření sady Visual Studio  
  
1.  Dvakrát klikněte `.vsix` souboru v Průzkumníku Windows, nebo jej otevřete v sadě Visual Studio.  
  
2.  Klikněte na tlačítko **nainstalovat** v dialogovém okně, které se zobrazí.  
  
3.  Chcete-li odinstalovat nebo dočasně zakázat rozšíření, otevřete **rozšíření a aktualizace** z **nástroje** nabídky.  
  
##  <a name="Localized"></a> Jak definovat lokalizované profily  
 Můžete definovat různé profily pro různé jazykové verze nebo jazyky a zabalit je do stejného rozšíření. Pokud uživatel načte vaše rozšíření, uvidí profil, který jste definovali pro jeho jazykovou verzi.  
  
 Vždy je nutné zadat výchozí profil. Pokud jste nedefinovali profil pro jazykovou verzi uživatele, zobrazí se výchozí profil.  
  
#### <a name="to-define-a-localized-profile"></a>Definování lokalizovaného profilu  
  
1.  Vytvořte profil, jak je popsáno v předchozích částech[jak definovat profil](#DefineProfile) a [tom, jak přidat profil do rozšíření aplikace Visual Studio](#AddProfile). Toto je výchozí profil a bude použit v jakékoli instalaci, pro kterou neposkytnete lokalizovaný profil.  
  
2.  Přidáte nový adresář ve stejném adresáři jako výchozí soubor profilu.  
  
    > [!NOTE]
    >  Pokud vytváříte rozšíření pomocí projektu rozšíření aplikace Visual Studio, přidejte novou složku do projektu pomocí Průzkumníka řešení.  
  
3.  Změňte název nového adresáře na krátký kód ISO pro lokalizovanou jazykovou verzi, například `bg` pro bulharštinu, nebo `fr` pro francouzštinu. Používejte neutrální jazykovou verzi kódu, obvykle dvě písmena, nikoli konkrétní jazykovou verzi jako `fr-CA`. Další informace o kódech jazykových najdete v tématu [CultureInfo.GetCultures metody](http://go.microsoft.com/fwlink/?LinkId=160782), která poskytuje úplný seznam kódů jazykových verzí.  
  
4.  Přidejte kopii výchozího profilu do nového adresáře. Neměňte jeho název souboru.  
  
     Ukázka [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] složku rozšíření, než je sestavena nebo komprimována do `.vsix` soubor, bude obsahovat následující složky a soubory:  
  
     `extension.vsixmanifest`  
  
     `MyProfile.profile`  
  
     `fr\MyProfile.profile`  
  
     `de\MyProfile.profile`  
  
    > [!NOTE]
    >  By neměl vkládat do `extension.vsixmanifest` odkaz na lokalizované verze profilů. Zkopírované soubory profilu musí mít stejný název jako profil v nadřazené složce.  
  
5.  Upravte novou kopii profilu, přitom přeložte do cílového jazyka všechny části, které budou viditelné pro uživatele, například `displayName` atributy.  
  
6.  Můžete vytvořit složky Další jazykové verze a lokalizované profily pro tolik jazykových verzí, kolik chcete.  
  
7.  Vytváření rozšíření sady Visual Studio sestavením rozšíření projektu nebo zkomprimováním všech souborů, jak je popsáno v předchozích částech.  
  
##  <a name="Schema"></a> Struktura profilu  
 Soubor XSD profilů UML lze najít v následující ukázce: [nastavení stereotypů a profilů XSD](http://go.microsoft.com/fwlink/?LinkID=213811). Při upravování souborů profilů snazší, nainstalujte `.xsd` v souboru:  
  
 **%ProgramFiles%\Microsoft visual Studio [verze] \Xml\Schemas**  
  
 Tato část používá profil C# jako příklad. Definici kompletního profilu si můžete prohlédnout ve:  
  
 *jednotky* **: \Program Files\Microsoft \Common7\IDE\Extensions\Microsoft\Architecture Tools\UmlProfiles\CSharp.profile sady Visual Studio [verze]**  
  
 První část této cesty se mohou lišit v instalaci.  
  
 Další informace o profilu .NET najdete v tématu [standardní Stereotypy pro modely UML](../modeling/standard-stereotypes-for-uml-models.md).  
  
### <a name="main-sections-of-the-uml-profile-definition"></a>Hlavní části definice profilu UML  
 Každý profil obsahuje následující obsah:  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<profile dslVersion="1.0.0.0"   
       name="CSharpProfile" displayName="C# Profile"   
       xmlns="http://schemas.microsoft.com/UML2.1.2/ProfileDefinition">  
  <stereotypes>...</stereotypes>  
  <metaclasses>...</metaclasses>  
  <propertyTypes>...</propertyTypes>  
</profile>  
```  
  
> [!NOTE]
>  Vlastnost nazvaná `name` nesmí obsahovat mezery ani interpunkci. Atribut `displayName`, která se zobrazí v uživatelském rozhraní, by měl být platný řetězec XML.  
  
 Každý profil obsahuje tři hlavní části. V opačném pořadí jsou následující:  
  
-   `<propertyTypes>` – seznam typů, které se používají pro vlastnosti definované v části stereotypů.  
  
-   `<metaclasses>` – seznam typů prvků modelu, na které stereotypy v tomto profilu použijí, například IClass, IInterface, IOperation, IDependency.  
  
-   `<stereotypes>` – definice stereotypů. Každá definice obsahuje názvy a typy vlastností, které jsou přidány do cílového elementu modelu.  
  
#### <a name="property-types"></a>Typy vlastností  
 `<propertyTypes>` Deklaruje seznam typů, které se používají pro vlastnosti v části `<stereotypes>` oddílu. Existují dva druhy typů vlastností: externí a výčet.  
  
 Externí typ deklaruje plně kvalifikovaný název typu .NET standard:  
  
```  
<externalType name="System.String" />  
```  
  
 Typ výčtu definuje sadu hodnot literálu:  
  
```  
<enumerationType name="PackageVisibility">  
  <enumerationLiterals>  
    <enumerationLiteral name="internal" displayName="internal"  />  
    <enumerationLiteral name="protectedinternal" displayName="protected internal" />  
  </enumerationLiterals>  
</enumerationType>  
```  
  
#### <a name="metaclasses"></a>Metatřídy  
 `<metaclasses>` Části je uveden seznam typů prvků modelu, na které lze definovat stereotypy v tomto profilu:  
  
```  
<metaclass   
      name="Microsoft.VisualStudio.Uml.Classes.IClass" />  
<metaclass  
      name="Microsoft.VisualStudio.Uml.Classes.IInterface" />  
<metaclass  
      name="Microsoft.VisualStudio.Uml.Components.IComponent" />  
```  
  
 Úplný seznam modelu element a typů vztahu, které lze použít jako metatřídy, viz [typy prvků modelu](#Elements).  
  
#### <a name="stereotype-definition"></a>Definice stereotypu  
 `<stereotypes>` Oddíl obsahuje jeden nebo více definic stereotypu:  
  
```  
<stereotype name="CSharpClass" displayName="C# Class"> ...  
```  
  
 Každý stereotyp uvádí jeden nebo více modelu element nebo typů vztahu, na které můžete použít. Můžete zadat název základního typu, chcete-li zahrnout všechny jeho odvozené typy. Pokud zadáte například `Microsoft.VisualStudio.Uml.Classes.IType`, stereotyp lze použít u `IClass`, `IInterface`, `IEnumeration`a několik dalších typů prvků.  
  
```  
<metaclasses>  
  <metaclassMoniker name=  
   "/CSharpProfile/Microsoft.VisualStudio.Uml.Classes.IClass" />  
</metaclasses>  
```  
  
 `name` Atribut `metaclassMoniker` je odkaz na prvek v `<metaClasses>` oddílu.  
  
> [!NOTE]
>  Zástupný název musí začínat `/yourProfileName/`, kde `yourProfileName` je definována v `name` profilu ("CSharpProfile" v tomto příkladu). Zástupný název končí názvem jedné z položek v části metatřídy.  
  
 Každý stereotyp může obsahovat seznam nula nebo více vlastností, které přidá k libovolnému prvku modelu, na který se použije. `<propertyType>` Obsahuje odkaz na jeden z typů, které jsou definovány v `<propertyTypes>` oddílu. Odkaz musí být buď `<externalTypeMoniker>` k odkazování na `<externalType>,` nebo `<enumerationTypeMoniker>` k odkazování na `<enumerationType>`. Opět odkaz začíná název vašeho profilu.  
  
```  
  <properties>  
    <property name="IsStatic"   
            displayName="Is Static" defaultValue="false">  
      <propertyType>  
<externalTypeMoniker   
               name="/CSharpProfile/System.Boolean" />  
      </propertyType>  
    </property>  
    <property name="PackageVisibility"   
              displayName="Package Visibility"  
              defaultValue="internal">  
      <propertyType>  
        <enumerationTypeMoniker   
              name="/CSharpProfile/PackageVisibility"/>  
      </propertyType>  
    </property>  
  </properties>  
</stereotype>  
```  
  
##  <a name="Elements"></a> Typy prvků modelu  
 Sada typů, pro které můžete definovat Stereotypy, je uvedena v [typy prvků modelu UML](../modeling/uml-model-element-types.md).  
  
## <a name="troubleshooting"></a>Poradce při potížích  
 Moje Stereotypy se nezobrazují mých modelech UML.  
 Musíte vybrat profil v balíčku nebo modelu. Stereotypy se pak objeví na prvcích uvnitř manifestu nebo modelu. Další informace najdete v tématu [elementům modelu UML Stereotypy přidat](../modeling/add-stereotypes-to-uml-model-elements.md).  
  
 Při otevření modelu UML se zobrazí následující chyba: **VS1707: následující profily nelze načíst, protože došlo k chybě serializace: MyProfile.profile**  
 1.  Ověřte správnost základní syntaxe XML souboru .profile.  
  
2. Zajistěte, aby byl každý název Monikeru v/ProfileName/nodename formuláři. ProfileName je hodnota atributu name v kořenovém uzlu profilu. NodeName je hodnota atributu name metatřídy, externalType nebo enumerationType.  
  
3. Zkontrolujte syntaxi je podle postupu popsaného tady a jak je ukázáno v _jednotky_**: \Program Files\Microsoft sady Visual Studio [verze] \Common7\IDE\Extensions\Microsoft\Architecture Tools\UmlProfiles\\** .  
  
4. Odinstalujte vadné rozšíření. Na **nástroje** nabídky, klikněte na tlačítko **rozšíření a aktualizace**.  
  
   -   Pokud rozšíření nezobrazí, viz další položka.  
  
5. Znovu soubor VSIX a otevřete ho v Průzkumníku Windows opětovně nainstalovat. Restartujte [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
   Rozšíření se nezobrazí ve Správci rozšíření, ale když se pokusíte znovu nainstalovat, zobrazí se následující zpráva: **rozšíření je již nainstalován na všech podporovaných produktů.**  
   1.  Odeberte soubor rozšíření z podsložky *LocalAppData*\Microsoft\VisualStudio\\\Extensions\ [verze]  
  
   -   Chcete-li zobrazit *LocalAppData*, je nutné nastavit zobrazit skryté soubory a složky v kartě Zobrazení možností složky Windows Explorer.  
  
   -   *LocalAppData* je obvykle v C:\Users\\*uživatelské jméno*\AppData\Local\  
  
6. Restartujte [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Viz také  
 [Přidávání stereotypů k elementům modelu UML](../modeling/add-stereotypes-to-uml-model-elements.md)   
 [Přizpůsobení modelu pomocí profilů a stereotypů](../modeling/customize-your-model-with-profiles-and-stereotypes.md)   
 [Standardní Stereotypy pro modely UML](../modeling/standard-stereotypes-for-uml-models.md)   
 [Ukázka: Barevné prvky UML podle stereotypu](http://go.microsoft.com/fwlink/?LinkID=213841)   
 [Ukázka: Nastavení stereotypů, profily XSD](http://go.microsoft.com/fwlink/?LinkID=213811)



