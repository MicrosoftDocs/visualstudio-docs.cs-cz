---
title: 'Návod: Vytvoření fragmentu kódu'
ms.date: 06/10/2019
ms.topic: conceptual
helpviewer_keywords:
- code snippets, creating
- code snippets, shortcut
- code snippets, template
- code snippets, replacements
- code snippets, references
- code snippets, imports
ms.assetid: 0dcaae11-39cf-4463-9c90-2494321251c2
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: adb0415e926bba9a1809c77f0f35b43d78263f43
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75597292"
---
# <a name="walkthrough-create-a-code-snippet"></a>Návod: Vytvoření fragmentu kódu

Fragment kódu můžete vytvořit pouze v několika krocích. Vše, co musíte udělat, je vytvořit soubor XML, vyplnit příslušné prvky a přidat do něj kód. Volitelně můžete použít náhradní parametry a odkazy na projekt. Importujte výstřižek do instalace sady Visual Studio pomocí tlačítka **Import ve** **Správci výstřižků kódu** **(Správce výstřižků kódu****nástrojů).** > 

## <a name="snippet-template"></a>Šablona úryvku

Základní šablona výstřižku je následující kód XML:

```xml
<?xml version="1.0" encoding="utf-8"?>
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
    <CodeSnippet Format="1.0.0">
        <Header>
            <Title></Title>
        </Header>
        <Snippet>
            <Code Language="">
                <![CDATA[]]>
            </Code>
        </Snippet>
    </CodeSnippet>
</CodeSnippets>
```

## <a name="create-a-code-snippet"></a>Vytvoření fragmentu kódu

1. Vytvořte nový soubor XML v sadě Visual Studio a přidejte výše uvedenou šablonu.

2. Vyplňte název výstřižku v elementu **Název.** Použijte název **odmocnina**.

3. Vyplňte jazyk úryvku v atributu **Language** elementu **Kód.** Pro C#použijte **CSharp**a Visual Basic použijte **VB**.

   > [!TIP]
   > Chcete-li zobrazit všechny dostupné hodnoty jazyka, projděte si [oddíl Atributy elementu Kód](code-snippets-schema-reference.md#attributes) na referenční stránce [schema fragmentů kódu.](code-snippets-schema-reference.md)

4. Přidejte kód úryvku v části **CDATA** uvnitř elementu **Code.**

   Pro C#:

   ```xml
   <Code Language="CSharp">
       <![CDATA[double root = Math.Sqrt(16);]]>
   </Code>
   ```

   Nebo pro visual basic:

   ```xml
   <Code Language="VB">
       <![CDATA[Dim root = Math.Sqrt(16)]]>
   </Code>
   ```

   > [!NOTE]
   > Nelze určit, jak mají být řádky kódu v části **CDATA** fragmentu kódu odsazeny nebo formátovány. Po vložení služba jazyka automaticky zformátuje vložený kód.

5. Uložte úryvek jako *SquareRoot.snippet* (můžete jej uložit kdekoli).

## <a name="import-a-code-snippet"></a>Import fragmentu kódu

1. Výstřižek můžete importovat do instalace sady Visual Studio pomocí **Správce výstřižků kódu**. Otevřete ji výběrem**Správce výstřižků kódu** **nástrojů** > .

2. Klepněte na tlačítko **Importovat.**

3. Přejděte do umístění, kam jste uložili fragment kódu v předchozím postupu, vyberte ho a klepněte na **otevřít**.

4. Otevře se dialogové okno **Importovat fragment kódu** s žádostí o výběr, kam chcete přidat úryvek z voleb v pravém podokně. Jednou z možností by měly být **výstřižky kódu**. Vyberte ji a klepněte na tlačítko **Dokončit**a potom **na ok**.

5. Úryvek se zkopíruje do jednoho z následujících umístění v závislosti na jazyku kódu:

   ::: moniker range="vs-2017"

   *%USERPROFILE%\Documents\Visual Studio 2017\Fragmenty kódu\Visual C#\Výstřižky*
   kódu *%USERPROFILE%\Documents\Visual Studio 2017\Fragmenty kódu\Visual Basic\Výstřižky kódu*

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   *%USERPROFILE%\Documents\Visual Studio 2019\Fragmenty kódu\Visual C#\Výstřižky*
   kódu *%USERPROFILE%\Documents\Visual Studio 2019\Fragmenty kódu\Visual Basic\Výstřižky kódu*

   ::: moniker-end

6. Otestujte fragment otevřením projektu jazyka C# nebo Visual Basic. Když je soubor kódu otevřený v editoru, zvolte **Fragmenty** > **vložit výstřižky** z nabídky po kliknutí pravým tlačítkem myši a potom **na Moje výstřižky kódu**. Měli byste vidět úryvek s názvem **Druhá odmocnina**. Poklepejte na něj.

   Kód fragmentu je vložen do souboru kódu.

## <a name="description-and-shortcut-fields"></a>Pole s popisem a zástupci

::: moniker range="vs-2017"

1. Pole popisu poskytují další informace o fragmentu kódu při zobrazení ve Správci výstřižků kódu. Zástupce je značka, kterou mohou uživatelé zadat za účelem vložení fragmentu. Přiěte nýtovaný soubor *%USERPROFILE%\Documents\Visual Studio 2017\Fragmenty\\kódu [Visual C# nebo Visual Basic]\Můj fragment kódu\SquareRoot.snippet*.

::: moniker-end

::: moniker range=">=vs-2019"

1. Pole popisu poskytují další informace o fragmentu kódu při zobrazení ve Správci výstřižků kódu. Zástupce je značka, kterou mohou uživatelé zadat za účelem vložení fragmentu. Přiěte nýtovaný soubor *%USERPROFILE%\Documents\Visual Studio 2019\Fragmenty\\kódu [Visual C# nebo Visual Basic]\Můj fragment kódu\SquareRoot.snippet*.

::: moniker-end

   > [!TIP]
   > Vzhledem k tomu, že upravujete soubor v adresáři, do kterého jej Sada Visual Studio umístila, nemusíte jej znovu importovat do sady Visual Studio.

2. Přidejte prvky **Autor** **a Popis** do elementu **Záhlaví** a vyplňte je.

3. Element **Header** by měl vypadat nějak takto:

   ```xml
   <Header>
       <Title>Square Root</Title>
       <Author>Myself</Author>
       <Description>Calculates the square root of 16.</Description>
   </Header>
   ```

4. Otevřete **Správce úryvků kódu** a vyberte fragment kódu. V pravém podokně si všimněte, že pole **Popis** a **Autor** jsou nyní vyplněna.

   ![Popis fragmentu kódu ve Správci fragmentů kódu](media/code-snippet-description-author.png)

5. Chcete-li přidat zástupce, přidejte prvek **Zástupce** do elementu **Záhlaví:**

   ```xml
   <Header>
      <Title>Square Root</Title>
      <Author>Myself</Author>
      <Description>Calculates the square root of 16.</Description>
      <Shortcut>sqrt</Shortcut>
    </Header>
   ```

6. Soubor úryvku znovu uložte.

7. Chcete-li zástupce otestovat, otevřete dříve použitý projekt, zadejte do editoru **sqrt** a stiskněte **klávesu Tab** (jednou pro jazyk Visual Basic, dvakrát pro C#).

   Je vložen kód fragmentu.

## <a name="replacement-parameters"></a>Náhradní parametry

Můžete chtít části fragmentu kódu, které mají být nahrazeny uživatelem. Můžete například chtít, aby uživatel nahradil název proměnné názvem v aktuálním projektu. Můžete zadat dva typy nahrazení: literály a objekty. Pomocí [elementu Literal](code-snippets-schema-reference.md#literal-element) k identifikaci náhrady za část kódu, která je zcela obsažena ve fragmentu, ale bude pravděpodobně přizpůsobena po vložení do kódu (například řetězec nebo číselná hodnota). Pomocí [elementu Object](code-snippets-schema-reference.md#object-element) můžete identifikovat položku, která je vyžadována fragmentem kódu, ale pravděpodobně bude definována mimo samotný výstřižek (například instanci objektu nebo ovládací prvek).

1. Chcete-li uživateli umožnit snadnou výměnu čísla pro výpočet druhé odmocniny, upravte prvek **Úryvek** souboru *SquareRoot.snippet* následujícím způsobem:

   ```xml
   <Snippet>
     <Code Language="CSharp">
       <![CDATA[double root = Math.Sqrt($Number$);]]>
     </Code>
     <Declarations>
       <Literal>
         <ID>Number</ID>
         <ToolTip>Choose the number you want the square root of.</ToolTip>
         <Default>16</Default>
       </Literal>
     </Declarations>
   </Snippet>
   ```

   Všimněte si, že nahrazení literálu je dáno ID (`Number`). Toto ID je odkazováno z fragmentu kódu `$` tím, že jej obklopuje znaky:

   ```xml
   <![CDATA[double root = Math.Sqrt($Number$);]]>
   ```

2. Uložte soubor úryvku.

3. Otevřete projekt a vložte fragment.

   Fragment kódu je vložen a upravitelný literál je zvýrazněn pro nahrazení. Najeďte nad parametr nahrazení, abyste viděli popisek pro hodnotu.

   ![Popisek parametru nahrazení fragmentu kódu v sadě Visual Studio](media/snippet-replacement-parameter-tooltip.png)

   > [!TIP]
   > Pokud je ve fragmentu více než jeden parametr odvetného stavu, můžete stisknutím **klávesy Tab** přejít z jednoho na druhý a změnit hodnoty.

## <a name="import-a-namespace"></a>Import oboru názvů

Fragment kódu můžete použít k přidání `using` direktivy `Imports` (C#) nebo příkazu (Visual Basic) zahrnutím [elementu Imports](code-snippets-schema-reference.md#imports-element). U projektů rozhraní .NET Framework můžete také přidat odkaz na projekt pomocí [elementu References](code-snippets-schema-reference.md#references-element).

Následující kód XML zobrazuje fragment kódu, který `File.Exists` používá metodu v System.IO oboru názvů, a proto definuje prvek **Imports** pro import System.IO oboru názvů.

```xml
<?xml version="1.0" encoding="utf-8"?>
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
  <CodeSnippet Format="1.0.0">
    <Header>
      <Title>File Exists</Title>
      <Shortcut>exists</Shortcut>
    </Header>
    <Snippet>
      <Code Language="CSharp">
        <![CDATA[var exists = File.Exists("C:\\Temp\\Notes.txt");]]>
      </Code>
      <Imports>
        <Import>
          <Namespace>System.IO</Namespace>
        </Import>
      </Imports>
    </Snippet>
  </CodeSnippet>
</CodeSnippets>
```

## <a name="see-also"></a>Viz také

- [Referenční informace ke schématu fragmentů kódu](../ide/code-snippets-schema-reference.md)
