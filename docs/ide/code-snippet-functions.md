---
title: Funkce fragmentu kódu
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- code snippets [Visual Studio], functions
- snippets [Visual Studio], functions
- IntelliSense code snippets, functions
ms.assetid: c0a2bf21-8fa5-4457-9281-f599beb53e7d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c7df85c429794d61028d5304108d289dfe9bf496
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594237"
---
# <a name="code-snippet-functions"></a>Funkce fragmentu kódu

K dispozici jsou tři funkce, které lze použít s fragmenty kódu jazyka C#. Funkce jsou určeny v prvku [Function](../ide/code-snippets-schema-reference.md#function-element) fragmentu kódu. Informace o vytváření výstřižků kódu naleznete v [tématu Fragmenty kódu](../ide/code-snippets.md).

## <a name="functions"></a>Funkce

Následující tabulka popisuje funkce, které jsou `Function` k dispozici pro použití s elementem ve výstřižcích kódu.

|Funkce|Popis|Jazyk|
|--------------|-----------------|--------------|
|`GenerateSwitchCases(EnumerationLiteral)`|Generuje switch příkaz a sadu case příkazy pro členy výčtu `EnumerationLiteral` určené parametrem. Parametr `EnumerationLiteral` musí být buď odkaz na výčet literálu nebo typ výčtu.|C#|
|`ClassName()`|Vrátí název třídy, která obsahuje vložený úryvek.|C#|
|`SimpleTypeName(TypeName)`|Redukuje *Parametr TypeName* na jeho nejjednodušší formu v kontextu, ve kterém byl vyvolán úryvek.|C#|

## <a name="generateswitchcases-example"></a>Příklad GenerateSwitchCases

Následující příklad ukazuje, jak `GenerateSwitchCases` používat funkci. Když je tento výstřižek vložen a výčet `$switch_on$` je zadán `$cases$` do literálu, literál generuje `case` příkaz pro každou hodnotu ve výčtu.

```xml
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
    <CodeSnippet Format="1.0.0">
        <Header>
            <Title>switch</Title>
            <Shortcut>switch</Shortcut>
            <Description>Code snippet for switch statement</Description>
            <Author>Microsoft Corporation</Author>
            <SnippetTypes>
                <SnippetType>Expansion</SnippetType>
            </SnippetTypes>
        </Header>
        <Snippet>
            <Declarations>
                <Literal>
                    <ID>expression</ID>
                    <ToolTip>Expression to switch on</ToolTip>
                    <Default>switch_on</Default>
                </Literal>
                <Literal Editable="false">
                    <ID>cases</ID>
                    <Function>GenerateSwitchCases($expression$)</Function>
                    <Default>default:</Default>
                </Literal>
            </Declarations>
            <Code Language="csharp">
                <![CDATA[
                    switch ($expression$)
                    {
                        $cases$
                    }
                ]]>
            </Code>
        </Snippet>
    </CodeSnippet>
</CodeSnippets>
```

## <a name="classname-example"></a>Příklad Názvu třídy

Následující příklad ukazuje, jak `ClassName` používat funkci. Po vložení tohoto úryvku `$classname$` je literál nahrazen názvem ohraničující třídy v tomto umístění v souboru kódu.

```xml
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
    <CodeSnippet Format="1.0.0">
        <Header>
            <Title>Common constructor pattern</Title>
            <Shortcut>ctor</Shortcut>
            <Description>Code Snippet for a constructor</Description>
            <Author>Microsoft Corporation</Author>
            <SnippetTypes>
                <SnippetType>Expansion</SnippetType>
            </SnippetTypes>
        </Header>
        <Snippet>
            <Declarations>
                <Literal>
                    <ID>type</ID>
                    <Default>int</Default>
                </Literal>
                <Literal>
                    <ID>name</ID>
                    <Default>field</Default>
                </Literal>
                <Literal default="true" Editable="false">
                    <ID>classname</ID>
                    <ToolTip>Class name</ToolTip>
                    <Function>ClassName()</Function>
                    <Default>ClassNamePlaceholder</Default>
                </Literal>
            </Declarations>
            <Code Language="csharp" Format="CData">
                <![CDATA[
                    public $classname$ ($type$ $name$)
                    {
                        this._$name$ = $name$;
                    }
                    private $type$ _$name$;
                ]]>
            </Code>
        </Snippet>
    </CodeSnippet>
</CodeSnippets>
```

## <a name="simpletypename-example"></a>Příklad SimpleTypeName

Tento příklad ukazuje, `SimpleTypeName` jak používat funkci. Když je tento úryvek vložen do `$SystemConsole$` souboru kódu, literál bude nahrazen <xref:System.Console> nejjednodušší formou typu v kontextu, ve kterém byl fragment vyvolán.

```xml
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
    <CodeSnippet Format="1.0.0">
        <Header>
            <Title>Console_WriteLine</Title>
            <Shortcut>cw</Shortcut>
            <Description>Code snippet for Console.WriteLine</Description>
            <Author>Microsoft Corporation</Author>
            <SnippetTypes>
                <SnippetType>Expansion</SnippetType>
            </SnippetTypes>
        </Header>
        <Snippet>
            <Declarations>
                <Literal Editable="false">
                    <ID>SystemConsole</ID>
                    <Function>SimpleTypeName(global::System.Console)</Function>
                </Literal>
            </Declarations>
            <Code Language="csharp">
                <![CDATA[
                    $SystemConsole$.WriteLine();
                ]]>
            </Code>
        </Snippet>
    </CodeSnippet>
</CodeSnippets>
```

## <a name="see-also"></a>Viz také

- [Funkční prvek](../ide/code-snippets-schema-reference.md#function-element)
- [Referenční informace ke schématu fragmentů kódu](../ide/code-snippets-schema-reference.md)
