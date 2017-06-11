
# Rules availables in eslint and tslint

|SONAR|TSLINT|ESLINT|
|---|---|---|
|[FunctionComplexity](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/FunctionComplexity.json)|cyclomatic-complexity|complexity|
|[DebuggerStatement](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/DebuggerStatement.json)|no-debugger|no-debugger|
|[EqEqEq](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/EqEqEq.json)|triple-equals|eqeqeq|
|[Eval](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/Eval.json)|no-eval|no-eval|
|[OneStatementPerLine](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/OneStatementPerLine.json)|one-variable-per-declaration|one-var|
|[Semicolon](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/Semicolon.json)|semicolon|semi|
|[CurlyBraces](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/CurlyBraces.json)|curly|curly|
|[BitwiseOperators](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/BitwiseOperators.json)|no-bitwise|no-bitwise|
|[PrimitiveWrappers](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/PrimitiveWrappers.json)|no-construct|no-new-wrappers|
|[ForIn](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/ForIn.json)|forin|guard-for-in|
|[FunctionDeclarationsWithinBlocks](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/FunctionDeclarationsWithinBlocks.json)|no-inner-declarations|no-inner-declarations|
|[TrailingComma](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/TrailingComma.json)|trailing-comma|comma-dangle|
|[AssignmentWithinCondition](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/AssignmentWithinCondition.json)|no-conditional-assignment|no-cond-assign|
|[LabelPlacement](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/LabelPlacement.json)|label-position|no-labels|
|[SwitchWithoutDefault](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/SwitchWithoutDefault.json)|switch-default|default-case|
|[NonEmptyCaseWithoutBreak](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/NonEmptyCaseWithoutBreak.json)|no-switch-case-fall-through|no-fallthrough|
|[EmptyBlock](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/EmptyBlock.json)|no-empty|no-empty|
|[TabCharacter](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/TabCharacter.json)|indent|indent|
|[BoundOrAssignedEvalOrArguments](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/BoundOrAssignedEvalOrArguments.json)|no-eval|no-eval|
|[VariableDeclarationAfterUsage](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/VariableDeclarationAfterUsage.json)|no-use-before-declare|no-use-before-define|
|[S1125](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/S1125.json)|no-extra-boolean-cast|no-extra-boolean-cast|
|[RedeclaredVariable](http://grepcode.com/file/repo1.maven.org/maven2/org.codehaus.sonar-plugins.javascript/javascript-checks/1.2/org/sonar/l10n/javascript/rules/javascript/RedeclaredVariable.html?av=f)|no-duplicate-variable|no-redeclare|
|[TrailingWhitespace](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/TrailingWhitespace.json)|no-trailing-whitespace|no-trailing-spaces|
|[S1442](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/S1442.json)|ban|no-alert|
|[S104](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/S104.json)|max-file-line-count|max-lines|

# Rules availables in eslint but currently unavailables in tslint

|SONAR|ESLINT|
|---|---|
|[WithStatement](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/WithStatement.json)|no-with|
|[MultilineStringLiterals](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/MultilineStringLiterals.json)|no-multi-str|
|[ArrayAndObjectConstructors](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/ArrayAndObjectConstructors.json)|no-new-object && no-array-constructor|
|[ExcessiveParameterList](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/ExcessiveParameterList.json)|max-params|
|[FunctionDefinitionInsideLoop](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/FunctionDefinitionInsideLoop.json)|no-loop-func|
|[S1135](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/S1135.json)|no-warning-comments|
|[TrailingComment](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/TrailingComment.json)|no-inline-comments|
|[S1134](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/S1134.json)|no-warning-comments|
|[S878](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/S878.json)|no-sequences|
|[NestedIfDepth](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/NestedIfDepth.json)|max-depth|


# Rules availables in eslint but not applicable to Typescript.

|SONAR|ESLINT|
|---|---|
|[UnreachableCode](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/UnreachableCode.json)|no-unreachable|
|[DuplicateFunctionArgument](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/DuplicateFunctionArgument.json)|no-dupe-args|
|[DuplicatePropertyName](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/DuplicatePropertyName.json)|no-dupe-keys|
|[OctalNumber](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/OctalNumber.json)|no-octal|
|[StrictMode](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/StrictMode.json)|strict|
|[UnusedVariable](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/UnusedVariable.json)|no-unused-vars [Deprecated]|

# Rules not available neither in tslint nor eslint

|SONAR|Descripción|
|---|---|
|[HtmlComments](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/HtmlComments.json)|HTML-style comments should not be used|
|[CollapsibleIfStatements](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/CollapsibleIfStatements.json)|Collapsible "if" statements should be merged|
|[ConstructorFunctionsForSideEffects](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/ConstructorFunctionsForSideEffects.json)|Objects should not be created to be dropped immediately without being used|
|[FutureReservedWords](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/FutureReservedWords.json)|"future reserved words" should not be used as identifiers|
|[ConditionalComment](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/ConditionalComment.json)|Internet Explorer's conditional comments should not be used|
|[S1145](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/S1145.json)|Useless "if(true) {...}" and "if(false){...}" blocks should be removed|
|[S138](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/S138.json)|Functions should not have too many lines|
|[RedeclaredFunction](http://grepcode.com/file/repo1.maven.org/maven2/org.codehaus.sonar-plugins.javascript/javascript-checks/1.2/org/sonar/l10n/javascript/rules/javascript/RedeclaredFunction.html?av=f)|This rule checks that functions declared in same scope don't have identical names.|
|[SameNameForFunctionAndVariable](http://grepcode.com/file/repo1.maven.org/maven2/org.codehaus.sonar-plugins.javascript/javascript-checks/1.2/org/sonar/l10n/javascript/rules/javascript/SameNameForFunctionAndVariable.html?av=f)|Declaring both a variable and a function with an identical name in same scope should be avoided.|
|[NamedFunctionExpression](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/NamedFunctionExpression.json)|Named function expressions should not be used|
|[TooManyBreakOrContinueInLoop](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/TooManyBreakOrContinueInLoop.json)|Loops should not contain more than a single "break" or "continue" statement|
|[UnusedFunctionArgument](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/UnusedFunctionArgument.json)|Unused function parameters should be removed|
|[S100](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/S100.json)|Function names should comply with a naming convention|
|[S1301](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/S1301.json)|"switch" statements should have at least 3 "case" clauses|
|[S1126](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/S1126.json)|Return of boolean expressions should not be wrapped into an "if-then-else" statement|
|[S1264](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/S1264.json)|A "while" loop should be used instead of a "for" loop|
|[S1472](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/S1472.json)|Function call arguments should not start on new lines|
|[S1219](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/S1219.json)|"switch" statements should not contain non-case labels|
|[S1067](https://github.com/SonarSource/sonar-javascript/blob/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript/S1067.json)|Expressions should not be too complex|

## Links

Sources:
- [Sonar Rules](http://grepcode.com/file/repo1.maven.org/maven2/org.codehaus.sonar-plugins.javascript/javascript-checks/1.2/org/sonar/l10n/javascript/rules/javascript/WithStatement.html?av=f)
- [Sonar Rules Repository](https://github.com/SonarSource/sonar-javascript/tree/master/javascript-checks/src/main/resources/org/sonar/l10n/javascript/rules/javascript)
- [TSLint rules](https://palantir.github.io/tslint/rules/)
- [ESLint rules](http://eslint.org/docs/rules/)

tslint-eslint-rules:
- [ESLint rules for TSLints - GitHub](https://github.com/buzinas/tslint-eslint-rules)
- [ESLint rules for TSLint - npm](https://www.npmjs.com/package/tslint-eslint-rules)
