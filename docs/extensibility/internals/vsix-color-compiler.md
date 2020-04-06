---
title: Překladač barev VSIX | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 99395da7-ec34-491d-9baa-0590d23283ce
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f414a56bb05a23b6efef19aa7c99292b8a40038a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703892"
---
# <a name="vsix-color-compiler"></a>Kompilátor barev VSIX
Nástroj Visual Studio Extension Color Compiler je konzolová aplikace, která přebírá soubor XML představující barvy pro existující motivy sady Visual Studio a zakrývá jej do souboru .pkgdef, aby tyto barvy mohly být použity v sadě Visual Studio. Vzhledem k tomu, že je snadné porovnat rozdíly mezi soubory XML, je tento nástroj užitečný pro správu vlastních barev ve správě zdrojového kódu. Může být také připojen do prostředí sestavení tak, aby výstup sestavení je platný soubor .pkgdef.

 **Schéma XML motivu**

 Úplný soubor XML motivu vypadá takto:

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

 Prvek \<motiv> definuje celý motiv. Motiv musí obsahovat alespoň \<jeden prvek kategorie>. Prvky motivu jsou definovány takto:

```xml
<Theme Name="name" GUID="guid">
      <!-- one or more Category elements -->
</Theme>
```

|||
|-|-|
|**Atribut**|**Definice**|
|Name (Název)|[Povinné] Název motivu|
|GUID|[Povinné] Identifikátor GUID motivu (musí odpovídat formátování GUID)|

 Při vytváření vlastních barev pro visual studio je třeba tyto barvy definovat pro následující motivy. Pokud pro určitý motiv neexistují žádné barvy, pokusí se visual studio načíst chybějící barvy z motivu Světlo.

|||
|-|-|
|**Název motivu**|**Guid motivu**|
|Světlý|{de3dbbcd-f642-433c-8353-8f1df4370aba}|
|Tmavý|{1ded0138-47ce-435e-84ef-9ec1f439b749}|
|Blue|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|
|Vysoký kontrast|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|

 **Kategorie**

 Prvek \<kategorie> definuje kolekci barev v motivu. Názvy kategorií poskytují logické seskupení a měly by být definovány co nejúžeji. Kategorie musí obsahovat alespoň \<jeden prvek Color>. Kategorie prvky jsou definovány takto:

```xml
<Category Name="name" GUID="guid">
      <!-- one or more Color elements -->
 </Category>
```

|||
|-|-|
|**Atribut**|**Definice**|
|Name (Název)|[Povinné] Název kategorie|
|GUID|[Povinné] Identifikátor GUID kategorie (musí odpovídat formátování GUID)|

 **Barev**

 Prvek \<Color> definuje barvu pro komponentu nebo stav ui. Upřednostňované schéma pojmenování barvy je [typ ui] [Stav]. Nepoužívejte slovo "barva", protože je nadbytečné. Barva by měla jasně označovat typ prvku a situace nebo "stav", pro který bude barva použita. Barva nesmí být prázdná a musí obsahovat \<jeden nebo \<oba> pozadí a prvek> popředí. Barevné prvky jsou definovány takto:

```xml
<Color Name="name">
        <Background /> <!-- zero or one Background element -->
        <Foreground /> <!-- zero or one Foreground element -->
 </Color>
```

|||
|-|-|
|**Atribut**|**Definice**|
|Name (Název)|[Povinné] Název barvy|

 **Pozadí a/nebo popředí**

 Prvky \<> \<pozadí a popředí> definují hodnotu a typ barvy pro pozadí nebo popředí prvku uživatelského rozhraní. Tyto prvky nemají děti.

```xml
<Background Type="type" Source="int" />
<Foreground Type="type" Source="int" />
```

|||
|-|-|
|**Atribut**|**Definice**|
|Typ|[Povinné] Typ barvy. Může to být jedna z následujících možností:<br /><br /> *CT_INVALID:* Barva je neplatná nebo není nastavena.<br /><br /> *CT_RAW:* Nezpracovaná hodnota ARGB.<br /><br /> *CT_COLORINDEX:* NEPOUŽÍVEJTE.<br /><br /> *CT_SYSCOLOR:* Barva systému Windows od syscolor.<br /><br /> *CT_VSCOLOR:* Barva visual ateliéru z __VSSYSCOLOREX.<br /><br /> *CT_AUTOMATIC:* Automatická barva.<br /><br /> *CT_TRACK_FOREGROUND:* NEPOUŽÍVEJTE.<br /><br /> *CT_TRACK_BACKGROUND:* NEPOUŽÍVEJTE.|
|Zdroj|[Povinné] Hodnota barvy reprezentované v šestnáctkovém čísle|

 Všechny hodnoty podporované __VSCOLORTYPE výčtu jsou podporovány schématem v atributu Type. Doporučujeme však používat pouze CT_RAW a CT_SYSCOLOR.

 **Všichni dohromady**

 Toto je jednoduchý příklad platného souboru XML motivu:

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

## <a name="how-to-use-the-tool"></a>Jak nástroj používat
 **Syntaxe**

 Soubor XML vsixColorCompiler \<> \<souboru PkgDef> \<volitelných> Args

 **Argumenty**

||||
|-|-|-|
|**Název přepínače**|**Poznámky**|**Povinné nebo volitelné**|
|Nepojmenovaný (soubor XML)|Toto je první nepojmenovaný parametr a cesta k souboru XML, který chcete převést.|Požaduje se|
|Nepojmenovaný (.pkgdef soubor)|Toto je druhý nepojmenovaný parametr a je výstupní cestou pro generovaný soubor .pkgdef.<br /><br /> Výchozí: \<Název souboru XML>.pkgdef|Nepovinné|
|/noLogo|Nastavení tohoto příznaku zabrání tisku informací o produktech a autorských právech.|Nepovinné|
|/?|Vytiskněte informace nápovědy.|Nepovinné|
|/help|Vytiskněte informace nápovědy.|Nepovinné|

 **Příklady**

- VsixColorCompiler D:\xml\colors.xml D:\pkgdef\colors.pkgdef

- VsixColorCompiler D:\xml\colors.xml /noLogo

## <a name="notes"></a>Poznámky

- Tento nástroj vyžaduje instalaci nejnovější verze runtime VC++.

- Podporovány jsou pouze jednotlivé soubory. Hromadný převod pomocí cest složek není podporován.

## <a name="sample-output"></a>Ukázkový výstup
 Soubor .pkgdef generovaný nástrojem bude podobný níže uvedené klávesy:

```
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\Environment]
"Data"=hex:3a,00,00,00,0b,00,00,00,01,00,00,00,c3,d9,4e,62,fd,bd,fa,41,96,c3,7c,82,4e,a3,2e,3d,01,00,00,00,0c,00,00,00,41,63,74,69,76,65,42,6f,72,64,65,72,01,cc,ce,db,ff,01,33,31,24,ff

[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\TreeView]
"Data"=hex:38,00,00,00,0b,00,00,00,01,00,00,00,8e,f0,ec,92,13,8b,f4,4c,99,e9,ae,26,92,38,21,85,01,00,00,00,0a,00,00,00,42,61,63,6b,67,72,6f,75,6e,64,01,f5,f5,f5,ff,01,1e,1e,1e,ff
```
