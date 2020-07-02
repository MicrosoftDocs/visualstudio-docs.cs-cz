---
title: Kompilátor barev VSIX | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 99395da7-ec34-491d-9baa-0590d23283ce
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5059a15c483f648c2248321c7ba8271a634d0c69
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85536094"
---
# <a name="vsix-color-compiler"></a>Kompilátor barev VSIX
Nástroj pro kompilátor barev rozšíření sady Visual Studio je Konzolová aplikace, která přebírá soubor. XML reprezentující barvy pro existující motivy sady Visual Studio a převede ho na soubor. pkgdef tak, aby tyto barvy mohly být použity v aplikaci Visual Studio. Vzhledem k tomu, že je snadné porovnat rozdíly mezi soubory. XML, tento nástroj je užitečný pro správu vlastních barev ve správě zdrojového kódu. Dá se taky připojit do prostředí pro Build, aby výstup buildu byl platný soubor. pkgdef.

 **Schéma XML motivu**

 Úplný soubor Theme. XML vypadá takto:

```xml
<Themes>
      <!—one or Theme elements -->
      <Theme>
        <!-- one or more Category elements -->
        <Category>
          <!-- one or more Color elements -->
          <Color>
            <!-- zero or one Background element -->
            <Background />
            <!-- zero or one Foreground element -->
            <Foreground />
          </Color>
        </Category>
      </Theme>
</Themes>
```

 **Motiv**

 \<Theme>Element definuje celý motiv. Motiv musí obsahovat alespoň jeden \<Category> element. Prvky motivu jsou definovány takto:

```xml
<Theme Name="name" GUID="guid">
      <!-- one or more Category elements -->
</Theme>
```

|**Atribut**|**Definice**|
|-|-|
|Name|Požadovanou Název motivu|
|Identifikátor GUID|Požadovanou Identifikátor GUID motivu (musí odpovídat formátování identifikátoru GUID)|

 Při vytváření vlastních barev pro aplikaci Visual Studio je nutné tyto barvy definovat pro následující motivy. Pokud pro určitý motiv neexistují žádné barvy, Visual Studio se pokusí načíst chybějící barvy z světlého motivu.

|**Název motivu**|**Identifikátor GUID motivu**|
|-|-|
|Světlý|{de3dbbcd-f642-433c-8353-8f1df4370aba}|
|Tmavý|{1ded0138-47ce-435e-84ef-9ec1f439b749}|
|Blue|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|
|Vysoký kontrast|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|

 **Kategorie**

 \<Category>Prvek definuje kolekci barev v motivu. Názvy kategorií poskytují logické seskupení a měly by být definovány co nejpřesněji. Kategorie musí obsahovat alespoň jeden \<Color> element. Prvky kategorie jsou definovány takto:

```xml
<Category Name="name" GUID="guid">
      <!-- one or more Color elements -->
 </Category>
```

|**Atribut**|**Definice**|
|-|-|
|Name|Požadovanou Název kategorie|
|Identifikátor GUID|Požadovanou Identifikátor GUID kategorie (musí odpovídat formátování identifikátoru GUID)|

 **Barva**

 \<Color>Element definuje barvu pro komponentu nebo stav uživatelského rozhraní. Upřednostňované schéma pojmenovávání barev je [typ uživatelského rozhraní] [stav]. Nepoužívejte slovo "Color", protože je redundantní. Barva by měla jasně označovat typ prvku a situace nebo "stát", pro který bude použita barva. Barva nesmí být prázdná a musí obsahovat buď jeden nebo oba \<Background> \<Foreground> elementy a. Barevné prvky jsou definovány takto:

```xml
<Color Name="name">
        <Background /> <!-- zero or one Background element -->
        <Foreground /> <!-- zero or one Foreground element -->
 </Color>
```

|**Atribut**|**Definice**|
|-|-|
|Name|Požadovanou Název barvy|

 **Pozadí a popředí**

 \<Background>Elementy a \<Foreground> definují hodnotu barvy a typ pro pozadí nebo popředí prvku uživatelského rozhraní. Tyto prvky nemají žádné podřízené položky.

```xml
<Background Type="type" Source="int" />
<Foreground Type="type" Source="int" />
```

|**Atribut**|**Definice**|
|-|-|
|Typ|Požadovanou Typ barvy. Může to být jedna z následujících:<br /><br /> *CT_INVALID:* Barva je neplatná nebo není nastavena.<br /><br /> *CT_RAW:* Nezpracovaná hodnota ARGB<br /><br /> *CT_COLORINDEX:* NEPOUŽÍVEJTE.<br /><br /> *CT_SYSCOLOR:* Systémová barva systému Windows z SysColor.<br /><br /> *CT_VSCOLOR:* Barva sady Visual Studio z __VSSYSCOLOREX.<br /><br /> *CT_AUTOMATIC:* Automatická barva.<br /><br /> *CT_TRACK_FOREGROUND:* NEPOUŽÍVEJTE.<br /><br /> *CT_TRACK_BACKGROUND:* NEPOUŽÍVEJTE.|
|Zdroj|Požadovanou Hodnota barvy reprezentovaná v šestnáctkovém formátu|

 Všechny hodnoty podporované výčtem __VSCOLORTYPE jsou podporovány schématem v atributu type. Doporučujeme však, abyste používali pouze CT_RAW a CT_SYSCOLOR.

 **Vše dohromady**

 Toto je jednoduchý příklad platného souboru Theme. XML:

```xml
<Themes>
  <Theme Name="Light" GUID="{de3dbbcd-f642-433c-8353-8f1df4370aba}">
    <Category Name="MyCategory" GUID="{0A96238B-70CE-4479-9170-EECEAA3FCD58}">
      <Color Name="MyActiveBorder">
        <Background Type="CT_RAW" Source="FFCCCEDB" />
      </Color>
    </Category>
  </Theme>
</Themes>
```

## <a name="how-to-use-the-tool"></a>Jak používat nástroj
 **Syntaxe**

 VsixColorCompiler \<XML file> \<PkgDef file>\<Optional Args>

 **Arguments**

|**Název přepínače**|**Poznámky**|**Povinné nebo volitelné**|
|-|-|-|
|Nepojmenované (soubor. XML)|Toto je první nepojmenovaný parametr a je cesta k souboru XML, který se má převést.|Vyžadováno|
|Nepojmenované (soubor. pkgdef)|Toto je druhý nepojmenovaný parametr a je výstupní cesta pro vygenerovaný soubor. pkgdef.<br /><br /> Výchozí: \<XML Filename> . pkgdef|Volitelné|
|/noLogo|Nastavením tohoto příznaku se zastaví tisk informací o produktech a copyrightech.|Volitelné|
|/?|Vytiskněte informace o nápovědě.|Volitelné|
|/help|Vytiskněte informace o nápovědě.|Volitelné|

 **Příklady**

- VsixColorCompiler D:\xml\colors.xml D:\pkgdef\colors.pkgdef

- VsixColorCompiler D:\xml\colors.xml/noLogo

## <a name="notes"></a>Poznámky

- Tento nástroj vyžaduje, aby byla nainstalovaná nejnovější verze modulu runtime VC + +.

- Jsou podporovány pouze jednotlivé soubory. Hromadný převod prostřednictvím cest ke složkám není podporován.

## <a name="sample-output"></a>Ukázkový výstup
 Soubor. pkgdef generovaný nástrojem bude vypadat podobně jako v následujících klíčích:

```
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\Environment]
"Data"=hex:3a,00,00,00,0b,00,00,00,01,00,00,00,c3,d9,4e,62,fd,bd,fa,41,96,c3,7c,82,4e,a3,2e,3d,01,00,00,00,0c,00,00,00,41,63,74,69,76,65,42,6f,72,64,65,72,01,cc,ce,db,ff,01,33,31,24,ff

[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\TreeView]
"Data"=hex:38,00,00,00,0b,00,00,00,01,00,00,00,8e,f0,ec,92,13,8b,f4,4c,99,e9,ae,26,92,38,21,85,01,00,00,00,0a,00,00,00,42,61,63,6b,67,72,6f,75,6e,64,01,f5,f5,f5,ff,01,1e,1e,1e,ff
```
