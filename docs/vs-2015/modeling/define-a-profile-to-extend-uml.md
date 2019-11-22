---
title: Definování profilu pro rozšiřování UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- profiles, UML
- stereotypes, UML
- UML, profiles and stereotypes
- UML - extending, defining profiles
- UML, customizing
- UML, profiles
ms.assetid: 776589cb-f89d-48d5-aafa-04a4c074b0d6
caps.latest.revision: 44
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bdb6620f8d73bf7fae7b7dbb1b92af38e71345b6
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295668"
---
# <a name="define-a-profile-to-extend-uml"></a>Definování profilu pro rozšíření UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete definovat *profil UML* pro přizpůsobení standardních prvků modelu pro konkrétní účely. Profil definuje jeden nebo více *stereotypů UML*. Stereotyp lze použít k označení typu, který představuje konkrétní druh objektu. Stereotyp může také roztáhnout seznam vlastností elementu.

 Několik profilů se instaluje s podporovanými edicemi sady Visual Studio. Chcete-li zjistit, které verze aplikace Visual Studio tuto funkci podporují, přečtěte si téma [podpora verzí pro nástroje pro architekturu a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport). Další informace o těchto profilech a o tom, jak použít stereotypy, najdete v tématu [Přizpůsobení modelu pomocí profilů a stereotypů](../modeling/customize-your-model-with-profiles-and-stereotypes.md).

 Můžete definovat vlastní profily pro přizpůsobení a rozšiřování UML do vlastní obchodní oblasti nebo architektury. Příklad:

- Pokud často definujete weby, můžete definovat vlastní profil, který poskytuje stereotyp «webová stránka», který lze použít na třídy v diagramech tříd. Pak můžete použít diagramy tříd k naplánování webu. Každá třída «webová stránka» by měla další vlastnosti pro obsah stránky, styl a tak dále.

- Pokud vyvíjíte bankovní software, můžete definovat profil, který poskytuje stereotyp «účet». Pak můžete použít diagramy tříd k definování různých typů účtu a zobrazení vztahů mezi nimi.

  Můžete distribuovat vlastní profily týmu. Každý člen týmu může nainstalovat váš profil. To jim umožní upravovat a vytvářet modely, které používají jeho stereotypy.

> [!NOTE]
> Pokud použijete Stereotypy profilu v modelu, který upravujete, a pak model nasdílíte s jinými lidmi, měli byste na své počítače nainstalovat stejný profil. V opačném případě nebudou moci zobrazit stereotypy, které jste použili.

 Profil je často součástí většího [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] rozšíření. Můžete například definovat příkaz, který přeloží některé části modelu na kód. Můžete definovat profil, který musí uživatelé použít na balíčky, které chtějí přeložit. Nový příkaz byste mohli distribuovat společně s profilem v jednom rozšíření [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].

 Můžete také definovat lokalizované varianty profilu. Uživatelé, kteří načítají vaše rozšíření, uvidí variantu, která je vhodná pro jejich vlastní jazykovou verzi.

## <a name="DefineProfile"></a>Jak definovat profil

#### <a name="to-define-a-uml-profile"></a>Definování profilu UML

1. Vytvořte nový soubor XML s příponou názvu souboru `.profile`.

2. Přidejte definice stereotypu podle pokynů popsaných ve [struktuře profilu](#Schema).

3. Přidejte profil do rozšíření sady Visual Studio (soubor`.vsix`). Můžete buď vytvořit nové rozšíření pro váš profil, nebo přidat profil k existujícímu rozšíření.

     Přečtěte si další část, [jak přidat profil do rozšíření sady Visual Studio](#AddProfile).

4. Nainstalujte do počítače rozšíření.

    1. Dvakrát klikněte na soubor rozšíření, který má příponu názvu souboru `.vsix`.

    2. Restartujte sadu Visual Studio.

5. Ověřte, zda byl profil nainstalován.

    1. Vyberte model v Průzkumníkovi UML.

    2. V okno Vlastnosti klikněte na vlastnost **profiles (profily** ). Váš profil se zobrazí v nabídce. Nastavte zaškrtnutí vedle profilu.

    3. Vyberte prvek, pro který váš profil definuje stereotypy. V okno Vlastnosti klikněte na vlastnost **Stereotypy** . Stereotypy se zobrazí v seznamu. Nastavte zaškrtnutí u jednoho ze stereotypů.

    4. Pokud váš profil definuje další vlastnosti pro tento stereotyp, rozbalte vlastnost stereotyp, aby se zobrazila.

6. Odešlete soubor rozšíření jiným uživatelům [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] k instalaci na jejich počítačích.

## <a name="AddProfile"></a>Postup přidání profilu do rozšíření sady Visual Studio
 Chcete-li nainstalovat profil a chcete-li jej odeslat ostatním uživatelům, je nutné přidat profil do rozšíření aplikace Visual Studio. Další informace najdete v tématu [nasazení rozšíření sady Visual Studio](https://go.microsoft.com/fwlink/?LinkId=160780).

#### <a name="to-define-a-profile-in-a-new-visual-studio-extension"></a>Definování profilu v novém rozšíření sady Visual Studio

1. Vytvořte projekt rozšíření aplikace Visual Studio.

   > [!NOTE]
   > Abyste mohli tento postup použít, musíte mít nainstalovanou [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)].

   1. V nabídce **soubor** přejděte na příkaz **Nový**a klikněte na **projekt**.

   2. V dialogovém okně **Nový projekt** rozbalte v části **Nainstalované šablony**možnost **vizuál C#** , klikněte na **rozšiřitelnost**a potom klikněte na **projekt VSIX**. Nastavte název projektu a klikněte na tlačítko **OK**.

2. Přidejte do projektu svůj profil.

   - V Průzkumník řešení klikněte pravým tlačítkem myši na projekt, přejděte na **Přidat**a pak klikněte na **existující položka**. V dialogovém okně vyhledejte soubor profilu.

3. Nastavte vlastnost **Kopírovat na výstupní** soubor profilu.

   1. V Průzkumník řešení klikněte pravým tlačítkem na soubor profilu a pak klikněte na **vlastnosti**.

   2. V okno Vlastnosti nastavte vlastnost **Kopírovat do výstupního adresáře** na **Kopírovat vždy**.

4. V Průzkumník řešení otevřete `source.extension.vsixmanifest`.

    Soubor se otevře v editoru manifestu rozšíření.

5. Na stránce **assets (prostředky** ) přidejte řádek popisující profil:

   - Klikněte na možnost **Nové**. Nastavte pole v dialogovém okně **Přidat nový prostředek** následujícím způsobem.

   - Nastavit **typ** na `Microsoft.VisualStudio.UmlProfile`

        Nejedná se o jednu z možností rozevíracího seznamu. Zadejte tento název z klávesnice.

   - Klikněte na **soubor v systému souborů** a vyberte název souboru profilu, například `MyProfile.profile`

6. Sestavte projekt.

7. **Chcete-li ladit profil**, stiskněte klávesu F5.

    Otevře se experimentální instance aplikace Visual Studio. V této instanci otevřete projekt modelování. V Průzkumníku UML vyberte kořenový prvek modelu a v okno Vlastnosti vyberte svůj profil. Pak vyberte prvky uvnitř modelu a nastavte stereotypy, které jsou pro ně definovány.

8. **Extrakce VSIX pro nasazení**

   1. V Průzkumníku Windows otevřete složku **.\bin\debug** nebo **.\bin\Release** a vyhledejte soubor **. vsix** . Toto je soubor rozšíření [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]. Může být nainstalováno do vašeho počítače a odesláno jiným uživatelům aplikace Visual Studio.

   2. Chcete-li nainstalovat rozšíření:

       1. Dvakrát klikněte na soubor `.vsix`. Spustí se instalační program rozšíření sady Visual Studio.

       2. Restartujte všechny instance sady Visual Studio, které jsou spuštěny.

   Následující alternativní postup lze použít pro malá rozšíření, pokud jste nenainstalovali [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)].

#### <a name="to-define-a-profile-extension-without-using-visual-studio-sdk"></a>Definování rozšíření profilu bez použití sady Visual Studio SDK

1. Vytvořte adresář Windows, který obsahuje následující tři soubory:

    - *YourProfile* `.profile`

    - `extension.vsixmanifest`

    - `[Content_Types].xml` – zadejte tento název, jak je znázorněno zde, a hranaté závorky

2. Upravte `[Content_Types].xml` tak, aby obsahovala následující text. Všimněte si, že obsahuje záznam pro každou příponu názvu souboru.

    ```
    <?xml version="1.0" encoding="utf-8"?>
    <Types xmlns="http://schemas.openxmlformats.org/package/2006/content-types">
      <Default Extension="profile" ContentType="application/octet-stream" />
      <Default Extension="vsixmanifest" ContentType="text/xml" />
    </Types>
    ```

3. Zkopírujte existující `extension.vsixmanifest` a upravte ji pomocí editoru XML. Změňte uzly ID, název a obsah.

    - V tomto adresáři můžete najít příklad `extension.vsixmanifest`:

         *jednotka* **: \Program Files\Microsoft Visual Studio [verze] \Common7\IDE\Extensions\Microsoft\Architecture Tools\UmlProfiles**

    - Uzel obsahu by měl vypadat takto:

        ```
        <Content>
          <CustomExtension Type="Microsoft.VisualStudio.UmlProfile"
          >YourProfile.Profile</CustomExtension>
        </Content>
        ```

4. Zkomprimujte tři soubory do souboru ZIP.

     V Průzkumníku Windows vyberte tři soubory, klikněte pravým tlačítkem myši, přejděte na **Odeslat do**a pak klikněte na **Komprimovaná složka (ZIP)** .

5. Přejmenujte soubor zip a změňte jeho příponu názvu z `.zip` na `.vsix`.

6. Chcete-li nainstalovat profil na libovolný počítač s odpovídajícími edicemi sady Visual Studio, dvakrát klikněte na soubor `.vsix`.

#### <a name="to-install-a-uml-profile-from-a-visual-studio-extension"></a>Instalace profilu UML z rozšíření sady Visual Studio

1. Dvakrát klikněte na soubor `.vsix` v Průzkumníkovi Windows nebo ho otevřete v sadě Visual Studio.

2. V dialogovém okně, které se zobrazí, klikněte na **nainstalovat** .

3. Chcete-li odinstalovat nebo dočasně zakázat rozšíření, otevřete **rozšíření a aktualizace** z nabídky **nástroje** .

## <a name="Localized"></a>Jak definovat lokalizované profily
 Můžete definovat různé profily pro různé jazykové verze nebo jazyky a zabalit je všechny do stejného rozšíření. Když uživatel načte vaše rozšíření, uvidí profil, který jste definovali pro jejich jazykovou verzi.

 Vždy je nutné zadat výchozí profil. Pokud jste pro jazykovou verzi uživatele nedefinovali profil, uvidí výchozí profil.

#### <a name="to-define-a-localized-profile"></a>Definování lokalizovaného profilu

1. Vytvořte profil, jak je popsáno v předchozích částech[jak definovat profil](#DefineProfile) a [jak přidat profil k rozšíření sady Visual Studio](#AddProfile). Toto je výchozí profil a bude použit v jakékoli instalaci, pro kterou neposkytnete lokalizovaný profil.

2. Přidejte nový adresář do stejného adresáře jako výchozí soubor profilu.

    > [!NOTE]
    > Pokud vytváříte rozšíření pomocí projektu rozšíření sady Visual Studio, použijte Průzkumník řešení k přidání nové složky do projektu.

3. Změňte název nového adresáře na krátký kód ISO pro lokalizovanou jazykovou verzi, jako je například `bg` pro bulharštinu nebo `fr` pro francouzštinu. Měli byste použít neutrální kód kultury, obvykle dvě písmena, nikoli konkrétní jazykovou verzi, například `fr-CA`. Další informace o kódech kultury naleznete v tématu [CultureInfo. GetCultures](https://go.microsoft.com/fwlink/?LinkId=160782), který poskytuje úplný seznam kódů jazykové verze.

4. Přidejte do nového adresáře kopii výchozího profilu. Neměňte název souboru.

     Ukázková složka rozšíření [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] před sestavením nebo kompresí do `.vsix` souboru by obsahovala následující složky a soubory:

     `extension.vsixmanifest`

     `MyProfile.profile`

     `fr\MyProfile.profile`

     `de\MyProfile.profile`

    > [!NOTE]
    > Nemusíte vkládat do `extension.vsixmanifest` odkaz na lokalizované verze profilů. Zkopírované soubory profilu musí mít stejný název jako profil v nadřazené složce.

5. Upravte novou kopii profilu a přeloží se na cílový jazyk na všechny části, které budou viditelné pro uživatele, například `displayName` atributy.

6. Můžete vytvořit další složky jazykové verze a lokalizované profily pro tolik kultur, kolik potřebujete.

7. Sestavte rozšíření sady Visual Studio, a to buď sestavením projektu rozšíření, nebo kompresí všech souborů, jak je popsáno v předchozích částech.

## <a name="Schema"></a>Struktura profilu
 Soubor XSD pro profily UML najdete v následující ukázce: [Nastavení stereotypů a profilů XSD](https://go.microsoft.com/fwlink/?LinkID=213811). Pro usnadnění úprav souborů profilu nainstalujte `.xsd` soubor v nástroji:

 **%ProgramFiles%\Microsoft Visual Studio [version]\Xml\Schemas**

 V této části se C# jako příklad používá profil. Úplnou definici profilu najdete v tématu:

 *jednotka* **: \Program Files\Microsoft Visual Studio [verze] \Common7\IDE\Extensions\Microsoft\Architecture Tools\UmlProfiles\CSharp.Profile**

 První části této cesty se můžou v instalaci lišit.

 Další informace o profilu .NET najdete v tématu [standardní stereotypy pro modely UML](../modeling/standard-stereotypes-for-uml-models.md).

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
> Atribut s názvem `name` nesmí obsahovat mezery ani interpunkční znaménka. Atribut `displayName`, který se zobrazí v uživatelském rozhraní, by měl být platným řetězcem XML.

 Každý profil obsahuje tři hlavní části. V opačném pořadí jsou následující:

- `<propertyTypes>` – seznam typů, které se používají pro vlastnosti definované v oddílu stereotypy.

- `<metaclasses>` – seznam typů prvků modelu, na které se stereotypy v tomto profilu vztahují, například IClass, IInterface, IOperation, IDependency.

- `<stereotypes>` – definice stereotypů. Každá definice zahrnuje názvy a typy vlastností, které jsou přidány do cílového prvku modelu.

#### <a name="property-types"></a>Typy vlastností
 Oddíl `<propertyTypes>` deklaruje seznam typů, které se používají pro vlastnosti v části `<stereotypes>`. Existují dva druhy typů vlastností: external a Enumeration.

 Externí typ deklaruje plně kvalifikovaný název standardního typu .NET:

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
 Oddíl `<metaclasses>` je seznam typů prvků modelu, na které lze definovat stereotypy v tomto profilu:

```
<metaclass
      name="Microsoft.VisualStudio.Uml.Classes.IClass" />
<metaclass
      name="Microsoft.VisualStudio.Uml.Classes.IInterface" />
<metaclass
      name="Microsoft.VisualStudio.Uml.Components.IComponent" />
```

 Úplný seznam elementů modelu a typů vztahů, které lze použít jako metatřídy, naleznete v tématu [typy prvků modelu](#Elements).

#### <a name="stereotype-definition"></a>Definice stereotypu
 Oddíl `<stereotypes>` obsahuje jednu nebo více definic stereotypu:

```
<stereotype name="CSharpClass" displayName="C# Class"> ...
```

 Jednotlivé stereotypy obsahují jeden nebo více elementů modelu nebo typů vztahů, na které lze použít. Můžete zadat název základního typu, chcete-li zahrnout všechny odvozené typy. Například pokud zadáte `Microsoft.VisualStudio.Uml.Classes.IType`, stereotyp lze použít na `IClass`, `IInterface`, `IEnumeration`a několik dalších typů prvků.

```
<metaclasses>
  <metaclassMoniker name=
   "/CSharpProfile/Microsoft.VisualStudio.Uml.Classes.IClass" />
</metaclasses>
```

 Atribut `name` `metaclassMoniker` je odkaz na prvek v oddílu `<metaClasses>`.

> [!NOTE]
> Název monikeru musí začínat na `/yourProfileName/`, kde `yourProfileName` je definovaný v atributu `name` profilu (v tomto příkladu "CSharpProfile"). Moniker končí názvem jedné z položek v oddílu metatřídy.

 Každý stereotyp může vypsat nula nebo více vlastností, které přidá do libovolného prvku modelu, na který je použit. `<propertyType>` obsahuje odkaz na jeden z typů, které jsou definovány v části `<propertyTypes>`. Odkaz musí být buď `<externalTypeMoniker>`, aby odkazoval na `<externalType>,` nebo `<enumerationTypeMoniker>`, aby odkazoval na `<enumerationType>`. Tento odkaz znovu začíná názvem vašeho profilu.

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

## <a name="Elements"></a>Typy prvků modelu
 Sada typů, pro které lze definovat stereotypy, je uvedena v [typech prvků modelu UML](../modeling/uml-model-element-types.md).

## <a name="troubleshooting"></a>Poradce při potížích
 Moje stereotypy se nezobrazují moje modely UML.
Musíte vybrat profil v balíčku nebo modelu. Stereotypy se pak zobrazí na prvcích uvnitř balíčku nebo modelu. Další informace najdete v tématu [Přidání stereotypů do prvků modelu UML](../modeling/add-stereotypes-to-uml-model-elements.md).

 Při otevření modelu UML se zobrazí následující chyba: **VS1707: následující profily nelze načíst, protože došlo k chybě serializace: myprofile. Profile**
1. Ověřte správnost syntaxe Basic XML profilu.

2. Zajistěte, aby byl každý název monikeru ve tvaru/profileName/nodeName. Název profilu je hodnota atributu name v uzlu root Profile. Node je hodnota atributu Name typu Metatřída, externalType nebo enumerationType.

3. Zajistěte, aby byla syntaxe popsaná zde, a jak je znázorněno v části _jednotka_ **: \Program Files\Microsoft Visual Studio [Version] \Common7\IDE\Extensions\Microsoft\Architecture Tools\UmlProfiles\\** .

4. Odinstalujte poškozenou příponu. Na **nástroje** nabídky, klikněte na tlačítko **rozšíření a aktualizace**.

   - Pokud se rozšíření nezobrazí, podívejte se na další položku.

5. Znovu sestavte soubor VSIX a otevřete ho v Průzkumníkovi Windows, abyste ho znovu nainstalovali. Restartujte [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

   Rozšíření se nezobrazuje ve Správci rozšíření, ale při pokusu o jeho opětovné instalaci se zobrazí následující zpráva: **rozšíření je již nainstalováno do všech příslušných produktů.**
   1. Odebrání souboru rozšíření z podsložky *localappdata*\Microsoft\VisualStudio\\[Version] \Extensions\

   - Chcete-li zobrazit *localappdata*, je třeba nastavit možnost Zobrazit skryté soubory a složky na kartě zobrazení možností složky v Průzkumníkovi Windows.

   - *Localappdata* je obvykle ve C:\Users\\*username*\AppData\Local\

6. Restartujte [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

## <a name="see-also"></a>Viz také
 [Přidání stereotypů do prvků modelu UML](../modeling/add-stereotypes-to-uml-model-elements.md) [Přizpůsobení modelu pomocí profilů a](../modeling/customize-your-model-with-profiles-and-stereotypes.md) [standardních stereotypů pro modely UML](../modeling/standard-stereotypes-for-uml-models.md) [Ukázka: barevné prvky UML podle stereotypu](https://go.microsoft.com/fwlink/?LinkID=213841) [Ukázka: nastavení stereotypů, profily XSD](https://go.microsoft.com/fwlink/?LinkID=213811)
