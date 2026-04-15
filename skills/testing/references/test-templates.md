# Test Templates

## Component contract test

```typescript
describe('[Component]', () => {
  // Contract: renders all variants
  it.each(['primary', 'secondary', 'ghost', 'destructive'])(
    'renders %s variant', (variant) => {
      render(<Component variant={variant} />);
      // assert variant-specific visual or structural difference
    }
  );

  // Contract: respects defaults
  it('applies default props from contract', () => {
    render(<Component />);
    // assert default variant, size, state
  });

  // Contract: accessibility
  it('meets a11y requirements', () => {
    render(<Component />);
    expect(screen.getByRole('button')).toHaveAttribute('tabIndex');
    // assert focus-visible, aria attributes per contract
  });

  // Contract: disabled state
  it('handles disabled state correctly', () => {
    render(<Component disabled />);
    expect(screen.getByRole('button')).toBeDisabled();
    // assert aria-disabled, visual indicator
  });

  // Contract: loading state
  it('shows loading indicator', () => {
    render(<Component loading />);
    // assert loading UI, disabled interaction
  });
});
```

## Interaction test
```typescript
it('handles full interaction cycle', async () => {
  const onAction = vi.fn();
  render(<Component onAction={onAction} />);

  // idle → hover
  await userEvent.hover(screen.getByRole('button'));
  // hover → click
  await userEvent.click(screen.getByRole('button'));
  expect(onAction).toHaveBeenCalledOnce();
});
```
