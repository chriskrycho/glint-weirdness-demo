# Glint LS behavior demo

This shows a quirky behavior that happens when you:

- set up a series of related projects (in this case with `composite: true`, but that is not necessary) where the projects include `glint` keys; and

- have a root `tsconfig.json` which *doesn’t* include a `glint` key, but which *is* the natural "owner" of some set of shared files which the other projects reference: here, the `types/index.d.ts`; and

- have the built-in TS disabled.

This works *fine* from a compilation model, and the references all work correctly in the sense of what the sub-projects see and how the server works with reference to them… but the LS doesn’t get activated at all by Code in the files which notionally are only covered by the root projecct.

To see this behavior, just open this project in VS Code, and notice that:

- `types/index.d.ts` gets no completions, no matter what…

- …but the things it provides are visible to the child projects (see `app/index.ts`)!
